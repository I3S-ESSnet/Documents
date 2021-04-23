# Cloud Platform Implementing the Blueprint

Table of Contents
=================

* [Cloud Platform Implementing the Blueprint](#cloud-platform-implementing-the-blueprint)
  * [From project description](#from-project-description)
  * [Containers](#containers)
    * [IS2 example](#is2-example)
    * [Application containerization](#application-containerization)
    * [Docker Compose](#docker-compose)
    * [Continuous integration](#continuous-integration)
      * [Travis CI](#travis-ci)
      * [Dockerhub](#dockerhub)
    * [PxWeb Example](#pxweb-example)
      * [Container](#container)
      * [Continuous integration](#continuous-integration-1)
        * [Travis CI](#travis-ci-1)
      * [Pipeline](#pipeline)
  * [Platform](#platform)
  * [Try the platform yourself](#try-the-platform-yourself)
    * [Create project and service\-account](#create-project-and-service-account)
    * [Create Kubernetes cluster](#create-kubernetes-cluster)
    * [Test Kubernetes cluster](#test-kubernetes-cluster)
    * [Install IS2 with Helm on Kubernetes](#install-is2-with-helm-on-kubernetes)
      * [Prerequisites](#prerequisites)
    * [Install IS2 with Helm on Kubernetes](#install-is2-with-helm-on-kubernetes-1)
      * [Prerequisites](#prerequisites-1)
    * [GCP Free Tier](#gcp-free-tier)
      * [Google Kubernetes Engine](#google-kubernetes-engine)
      * [Compute Engine](#compute-engine)
    * [SSL](#ssl)
      * [Adding TLS](#adding-tls)
      * [Renew certificates](#renew-certificates)
    * [PxWeb](#pxweb)
  * [Links](#links)
## From project description
The platform will use a standard solution like, for example, Amazon Web Services, Microsoft Azure or Google Cloud Platform.

(Structure and eventually reference to delivery slip for "infrastructure as code")



## Containers

### IS2 example
During the Rome hackathon the Istat application IS2 was containerized. IS2 is a standard Java, Spring Boot web application with a PostgrSQL database. https://github.com/mecdcme/is2

We forked the application and created [Dockerfiles](https://docs.docker.com/engine/reference/builder/) for the database and application.

Database containerization
The `db.Dockerfile` is very simple. The initdb script was already in the existing repository.

```Dockerfile
FROM postgres:11
COPY ./db/is2-postgres.sql /docker-entrypoint-initdb.d/
```

With this dockerfile, we can create and run the dockerimage like this:

```Shell
docker build -t mecdcme/is2-postgres . -f db.Dockerfile
docker run -p 5432:5432 mecdcme/is2-postgres
```

### Application containerization
For the application we take advantage of the [multi-stage build feature in Docker](https://docs.docker.com/develop/develop-images/multistage-build/).  With this Dockerfile we both build the IS2 application with maven AND we create the docker image

```Dockerfile
FROM maven:3.6-jdk-11 AS build
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package
FROM openjdk:11-jdk-slim
COPY --from=build /usr/src/app/target/is2.jar /usr/app/is2.jar
RUN mkdir -p /usr/app/is2/RScripts
COPY RScripts /usr/app/is2/RScripts
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/app/is2.jar"]
```

With this dockerfile, we can create and run the dockerimage like this:

```Shell
docker build -t mecdcme/is2 .
docker run -p 8080:8080 mecdcme/is2 
```

### Docker Compose
The IS2 application is now a multi-container application. To run these two containers and enable them to talk to each other we use [Docker Compose](https://docs.docker.com/compose/). The docker-compose.yml file looks like this:

```YAML
version: '3'
services:
  app:
    image: mecdcme/is2:latest
    ports:
      - 8080:8080
    environment:
      - SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/postgres?currentSchema=is2
      - SPRING_DATASOURCE_USERNAME=postgres
      - SPRING_DATASOURCE_PASSWORD=postgres
      - SPRING_DATASOURCE_DRIVERCLASSNAME=org.postgresql.Driver
      - SPRING_DATASOURCE_PLATFORM=postgresql
    depends_on:
      - db
    restart: always
  db:
    image: mecdcme/is2-postgres:latest
    environment:
      - POSTGRES_PASSWORD=postgres
  adminer:
    image: adminer
    restart: always
    ports:
      - 8081:8080
```


Start both containers with this single command:

```Shell
docker-compose up
```

### Continuous integration

#### Travis CI
With open-source applications on Github there are many free tools for doing continuous integration. We set up Travis CI for building the application.

.travis.yml
```YAML
language: java
jdk: openjdk11

addons: 
  sonarcloud:
    organisation: "mecdcme"
    token:
      secure: ***

script:
  - mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install sonar:sonar -Dsonar.projectKey=mecdcme_is2
```

Results at https://travis-ci.org/github/mecdcme/is2

#### Dockerhub
Docker also offer a free service for open source prosjects. We have set up automatic building of images on Dockerhub https://cloud.docker.com/u/mecdcme/

### PxWeb Example

The current version of PxWeb is a legacy ASP.NET 4.6 application. SCB wil port it to ASP.NET Core but until then we wanted to try containerize the current verison. PxWeb was open sourced in August 2019 https://github.com/statisticssweden/PxWeb and forked to https://github.com/I3S-ESSnet/PxWeb 

#### Container
Since PxWeb is a ASP.NET 4.X application the docker image must be build and run on a Windows host.

```Dockerfile
FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-1803 as build
WORKDIR /temp/PxWeb
COPY . .
RUN nuget restore
RUN msbuild /p:Configuration=Release PXWeb/PXWeb.csproj /p:DeployOnBuild=true /p:PublishProfile=filesystem.pubxml

FROM mcr.microsoft.com/dotnet/framework/aspnet:4.7.2-windowsservercore-1803
WORKDIR /inetpub/wwwroot
COPY --from=build /temp/build/. ./
```

Build and run
```
docker build -t pxweb .
docker run -p 80:80 pxweb
```

#### Continuous integration

##### Travis CI

This example builds the Windows container on Travis and publish it on Dockerhub.


> **_NOTE:_**
When using docker images that require Windows hosts.
Travis only support Windows Server, version 1803. 
Github Actions only support Windows Server 2019 and Windows Server 2016 R2
You have to be  aware of this when choosing online services.


The username and password for Dockerhub is encrypted and will break when the repository is forked on GitHub. For more details see https://docs.travis-ci.com/user/environment-variables/#defining-encrypted-variables-in-travisyml

.travis.yml
```YAML
language: shell
os: windows
services: docker

env:
  global:
    - secure: x5Eq9lqHCEXXx5wOuJkHhE/0FUNtEw/RfgJzPHgf3EN23DilrpNkujFwArQawE8GiCkJuxEvssnaOTqNIy1KQ/beSwI/kaOjgiyfIIq+H9nm9k781JnUKIRtHpK9m1dRqv3R7CFDAq3X/n4onliA/BVRBBEVD3GAJ8/Z2+RkFVZvtnyn4F1Atci5tXC/LfgFnwdwyN0PT0dNFmQ0eg6fvhRTF/u9J+yB5Q0Y1BiU6ENDwra2eYfhvDbo0Vl1iQCHR316kOVDG0M0KFot9Ufk9ZW/LAJ0sNgvgnXMgBmnk6d4YH/7PFvqOFIlSfX49gx4VPWnqpIx2G9w8rJImwQNdssTaBf/3vToUay0Mml1Tr8fTLtVgAm0qt1+YK5eZPJjYUoQ/Qffr/rk+voVAkPPtacbmYAQTlM8EZwY3OzZrslsK41lFjU66mit9lnVfcDkW9amG21UWUa9RFiNGKlRc6uUHS1CHlmbeDCUd7QKjsBhvQKFaI8bD92TEAEiASiqRmuy6f468hKuTHEFgsTUUs1z2IMx00SzafAMXRz4jEU47CAdIEleXpyoXTkeKTeGFFYbqKepjo578gcPHfZhYYmqtS2RCPQadV9Cf9UCYCHgyD6bTd5T950bNnfUP73x3BNiHExVr0GD6mW6JE3lXMOLzqSybC093uSYXNGQ9kE=
    - secure: BIgJiXc9JuewbHUYLIMgjh72bYsAI8N3Hu918f5qGDn0QWGHkMG57eMwn1zpu/kV6vm6wqG97MJCLVOvYudmxtOVOkF4wTaVvV3sicQmPWbf9QQct1Cn3mjcCAIwH55HGGstodJhRtbWW9FTZhmjzKW8FS+iS/RWOC3aKRsGHTKnMK4yy2Sb92WbBQ1Sbs3qjYBUshFcSiFIpezQcHYfk8FUILVNhTz39KLzxkpQw4oJqiMksqFLCjWRpU6ZLzQoV2aKT0XeIJsYNYRppTM20byuHfyGKqKHnPmIfyTT2wW3Dt+QTkj3H710CgAvRvJBN7iZKCU5TiMYTWh0tfcTb9M7FU/ZCoNzOvTbAZZ3tOWvGdgc0TuoF0Y9EoOQS13RdRXraMNdCzN4h1RhIXByTTqMxlI+uNwCE9Cc3A4gduXLzWqlir+SG33tjhHzrK15EBs/6d1G9zUO3bfUbsMHf8LubWjxiDNWr7O3cGsybUOCPOy9eWn3TppIXXxgXBAtNUgv46uZQKOhkNnI3wSoLhqo+X3KxVU/gcEO9L74Zh30A3ceQ4ghRGxZTxcvK0ptFTWTsYT8zwzFw5iqRWsIp/qHvk7pVGeWju7cKLjamY8Pxi4lQgUa/PT7YuvYiJRHhffBjp4lwqZG3EOH0cMWi2GqZz//68aqvnLoLUrcs+w=

script:
  - docker build --tag "${DOCKER_USERNAME}/pxweb:latest" .

after_script:
  - docker images

before_deploy:
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
  - docker tag "${DOCKER_USERNAME}/pxweb:latest" "${DOCKER_USERNAME}/pxweb:windowsservercore-1803"

deploy:
  provider: script
  script: docker push "${DOCKER_USERNAME}/pxweb:latest" && docker push "${DOCKER_USERNAME}/pxweb:windowsservercore-1803"
  on:
    branch: master
    all_branches: true
```

#### Pipeline
![alt text](pxweb1.png "PxWeb pipeline")


## Platform Deployathons
We arranged a series of events called "Deployathons" to make a real platform and deploy [IS2](https://github.com/mecdcme/is2) and [ARC](https://github.com/InseeFr/ARC) using state of the art solutions.
### Participants

* France: Oliver Levitt, Donatien Enneman, Romain Tailhurat, Manu Soulier
* Norway: Rune Johansen, Trygve Falch
* Italy: Mauro Bruno, Francesco Amato

### Building the platform
The first part of the job is to set up a container platform. We make the easy choice: [Kubernetes](https://kubernetes.io/). Moreover, it will be Kubernetes (a.k.a k8s or Kube) on [GCP](https://cloud.google.com/) using Google's managed Kubernetes service : [GKE](https://cloud.google.com/kubernetes-engine/).  Managed Kubernetes means that the cloud provider handles most of the configuration. Kubernetes is also installable on-premise with a little more work not covered here (see [Kubespray](https://github.com/kubernetes-sigs/kubespray) or [Openshift](https://www.openshift.com/) for on-premise alternatives).



### Terraform

[Terraform](https://www.terraform.io/) is one of the leading [infrastructure-as-code](https://en.wikipedia.org/wiki/Infrastructure_as_code) solution nowadays.

The GKE managed service takes care of the master nodes. We only have to create and provision worker nodes.
Because the worker nodes are the ones that are use for computation they must be rightfully sized. 

Here, we choose a pool of three worker nodes. 

:warning: Those are preemptible nodes, i.e. that are short-lived and could be recycled at any times. See [running preemptible VMs](https://cloud.google.com/kubernetes-engine/docs/how-to/preemptible-vms) for more details. This is less of an issue than you may anticipate as resilience is done at scale on a Kubernetes cluster. Nonetheless, production-grade clusters should probably avoid running only preemptible nodes.

```javascript=
resource "google_container_node_pool" "primary_preemptible_nodes" {
  name       = "my-node-pool"
  location   = "europe-west1-b"
  cluster    = google_container_cluster.primary.name
  node_count = 3
  management {
     auto_repair = true
     auto_upgrade = true
  }

  node_config {
    preemptible  = true
    machine_type = "e2-small"
    
    [...]
  }
}
```  


### Google Kubernetes Engine (GKE) Pricing
Pricing can be confucing so we will try to explain it. 

Google offers [Free Tier](https://cloud.google.com/free) but Kubernetes Node pools of `f1-micro` machines are not supported due to insufficient memory. What is free, is the cluster management fee for your first cluster.

> **One Autopilot or Zonal cluster per month**
>
> One-click container orchestration via Kubernetes clusters, managed by Google.
>
> No cluster management fee for one Autopilot or Zonal cluster per billing account
> For clusters created in Autopilot mode, pods are billed per second for vCPU, memory, and > disk resource requests
> For clusters created in Standard mode, each user node is charged at standard Compute Engine pricing

FYI in february 2021 after the last deployaton, Google launched [GKE Autopilot](https://cloud.google.com/blog/products/containers-kubernetes/introducing-gke-autopilot). Examples in this document uses GKE Standard 




## Try the platform yourself

* Fork this repo on Github https://github.com/I3S-ESSnet/Platform
* Sign up for free on https://cloud.google.com/
* install Google Cloud SDK https://cloud.google.com/sdk/docs/install

### Create project and service-account

```sh
gcloud auth login
gcloud projects create i3s-ninja
gcloud config set project i3s-ninja
gcloud iam service-accounts create terraform
gcloud projects add-iam-policy-binding i3s-ninja --member "serviceAccount:terraform@i3s-$ $ ninja.iam.gserviceaccount.com" --role "roles/owner"
gcloud iam service-accounts keys create account.json --iam-account "terraform@i3s-$ ninja.iam.gserviceaccount.com"
```

### Create Kubernetes cluster

* install Terraform CLI https://www.terraform.io/downloads.html

```sh
$ terraform version
Terraform v0.14.8
+ provider registry.terraform.io/hashicorp/google v3.59.0
+ provider registry.terraform.io/hashicorp/kubernetes v2.0.2

$ terraform init
$ terraform plan -out "run.plan"
$ terraform apply "run.plan"
```
flow links in initial error messages to enable "Kubernetes Engine API"
Even if it is FREE it requires av billing account.

### Test Kubernetes cluster

* install kubectl https://kubernetes.io/docs/tasks/tools/#kubectl

````sh
$ gcloud container clusters get-credentials i3s-standard-cluster --region europe-west1-b

$ kubectl get nodes                                                                     
NAME                                                  STATUS   ROLES    AGE   VERSION
gke-i3s-standard-clus-first-node-pool-82c76e25-4cqk   Ready    <none>   23m   v1.18.16-gke.502
gke-i3s-standard-clus-first-node-pool-82c76e25-cm76   Ready    <none>   23m   v1.18.16-gke.502
````

### Install IS2 with Helm on Kubernetes

#### Prerequisites
* install helm https://helm.sh/docs/intro/install/
* clone https://github.com/mecdcme/is2




````sh
$ cd is2/helm
$ helm install --create-namespace --namespace is2 is2 .
````

````sh
$ cd apps/nginx-ingress
$ helm dependencies update
$ helm install --create-namespace --namespace nginx-ingress nginx-ingress .

$ export NGINX_INGRESS_IP=$(kubectl get service -n nginx-ingress nginx-ingress-ingress-nginx-controller -ojson | jq -r '.status.loadBalancer.ingress[].ip')\n
$ echo $NGINX_INGRESS_IP
34.78.199.11

 helm upgrade -n is2 is2 . -f values.yaml
 helm get values -n is2 is2
 helm uninstall -n is2 is2 
 
````

### Install IS2 with Helm on Kubernetes
#### Prerequisites
* install helm https://helm.sh/docs/intro/install/
* clone https://github.com/InseeFr/ARC

````sh
cd ARC/helm
# adjust values.yaml
helm install --create-namespace --namespace arc arc .


````



### SSL

#### Adding TLS
...
#### Renew certificates
````sh
$ kubectl delete secret wildcard -n nginx-ingress
$ kubectl create secret tls wildcard --key privkey.pem --cert fullchain.pem -n nginx-ingress
````

### PxWeb

THIS NEEDS REWRITE

We want to use [Terraform](https://www.terraform.io/) to provision hardware.
The first example is working great. Se second is not working yet, because the
Windows container require some more parameters.

* [Azure App Service](https://github.com/I3S-ESSnet/PxWeb/tree/master/terraform/azurerm/app-service)
* [Azure Kubernetes Service](https://github.com/I3S-ESSnet/PxWeb/tree/master/terraform/azurerm/kubernetes)



## Links
* Notes from deployathons: https://web.archive.org/web/20210423075000/https://hackmd.io/1aWd6CawSyKSI0fiMCkD2A
* https://web.archive.org/web/20210422234949/https://docs.docker.com/compose/
* https://github.com/InseeFrLab/cloud-scripts/tree/master/gke

