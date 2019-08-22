# Blueprint for I3S


## Background
Based on the work done in WP2, and using modern application architecture patterns we want to create a blueprint for a reference runtime environment for modern, sharable services following CSPA standards/principles using containers. This work package will describe the basic infrastructure needed, and implement a cloud instance for the needs of the ESSnet. The infrastructure will be documented as code, which will give to its users the opportunity to version it, and fork it. Typical products implementing this pattern would be Ansible Playbook or Terraform. Using the “infrastructure as a code” model will enable NSIs to easily create their own modern infrastructure on their premises. There will also be provided, as part of this WP a simple container-based platform using a cloud infrastructure, which will allow to validate the blueprint and to perform functional tests on the services developed in WP1, as well as validate their packaging and installation.

Retro-fitted, and modularized existing services will also be tested on the platform,either on premise or on the public cloud instance. This work package will also explore security components like IAM (Identity and Access Management), OAuth 2.0 and OPA (Open Policy Agent) for authentication and authorization, or Service Mesh for routing and secure service-to-service communication, for authentication and authorization. The WP will also look into how this type of security components can be added to existing services. Containerization and orchestration technologies, including Kubernetes and Docker, will be the basis of the platform, and all other infrastructure components will be built with it or around it.
Prerequisite
For starting to build services that you want to containerize, you will need a machine that can run Docker as a minimum, or a virtual machine that runs docker. There are also several online options for running containerized services. They greatly vary in price and functionality but can be used as a test for running simple services in the cloud (or on premise).

In general it’s hard to establish and maintain an on-premise, container platform from scratch, depending on your organizations maturity. But there are several good on premise platform-products that will help you with things like security and hardware provisioning, like Apache Mesos, and RedHat OpenShift.

## Containerization
There are several container initiatives, but the one that has been there longest, and have the largest adoption is Docker.  The container format is being standardized as part of the OCI (Open Container Initiative). Containerization is basically a way of creating a small virtual computer, that contains only the virtualized hardware required for the application you want to run, so it works as a way of transporting services without your application having to know anything about the environment around it. This is also its greatest challenge. In WP2 there will be described a lot of architectural guidelines for how you should design your application to make it scalable, and secure, so this document will only reference that work.
Environment
You can run Docker either on a Windows machine, or a Linux/Mac. Even .Net applications in containers are moving towards running on Linux host-systems, so for minimal pain, you should set up your docker environment on a linux machine, or in a virtual machine running linux. We provide pre-designed virtual environments which have Docker pre-installed which can be used to set up your environment
On premise
For test purposes it should be sufficient to use a standard Docker installation for getting things up and running. For production quality runtime environments for containers and for container orchestration we recommend looking into products like Apache Mesos or RedHat OpenShift.

(*is Docker Swarm also an alternative?*)

## Cloud
* Google Cloud Kubernetes
* Azure Kubernetes Service
* Amazon EC2, Amason EKS.

## Considerations

...

# Appendix


## IS2 example
During the Rome hackathon the Istat application IS2 was containerized. IS2 is a standard Java, Spring Boot web application with a MySQL database. https://github.com/mecdcme/is2

We forked the application to the I3S repository https://github.com/I3S-ESSnet/is2 and created Dockerfiles for the database and application.

Database containerization
The `db.Dockerfile` is very simple. The initdb script was already in the existing repository.

```FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD root
ENV MYSQL_DATABSE IS2
COPY ./db/is2.sql /docker-entrypoint-initdb.d/
```

With this dockerfile, we can create and run the dockerimage like this:

```$ docker build -t i3sessnet/is2-mysql . -f db.Dockerfile
$ docker run -p 3306:3306 i3sessnet/is2-mysql
```

## Application containerization
For the application we take advantage of the multi-stage build feature in Docker.  With this app.Dockerfile we both build the IS2 application with maven AND we create the docker image

```FROM maven:3.6-jdk-8-alpine AS build
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn -f /usr/src/app/pom.xml clean package
FROM openjdk:8-jdk-alpine
ENV SPRING_JPA_PROPERTIES_HIBERNATE_DIALECT org.hibernate.dialect.MySQLDialect
ENV SPRING_DATASOURCE_URL jdbc:mysql://localhost:3306/IS2?allowPublicKeyRetrieval=true&useSSL=false&useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC
COPY --from=build /usr/src/app/target/is2.jar /usr/app/is2.jar
COPY wait-for /usr/app/wait-for
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/app/is2.jar"]
```

With this dockerfile, we can create and run the dockerimage like this:

```$ docker build -t i3sessnet/is2 . -f app.Dockerfile
$ docker run -p 8080:8080 i3sessnet/is2
```

## Docker Compose
The IS2 application is now a multi-container application. To run these two containers and enable them to talk to each other we use Docker Compose. The docker-compose.yml file looks like this:

```version: '3'
services:
  app:
    image: i3sessnet/is2:latest
    entrypoint: ["/usr/app/wait-for", "--timeout=60", "db:3306", "--", "java", "-jar", "/usr/app/is2.jar"]
    ports:
      - 8080:8080
    environment:
      - SPRING_DATASOURCE_URL=jdbc:mysql://db:3306/IS2?
allowPublicKeyRetrieval=true&useSSL=false&useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC&autoReconnect=true
    depends_on:
      - db
  db:
    image: i3sessnet/is2-mysql:latest
    command: mysqld --default-authentication-plugin=mysql_native_password
```

One note on the strange looking entrypoint. The current application will crash if there is no database present at startup.  Even if there is a depends_on relation between the services, the application will not wait for the database. With this wait-for we can force the application to wait for a period of time.

Start both containers with this single command:

```$ docker-compose up```

## Continuous integration

### Travis CI
With open-source applications on Github there are many free tools for doing continuous integration. We set up Travis CI for building both docker images.

```.travis.yml
language: java
services:
- docker
before_install:
- docker build -t i3sessnet/is2 -f app.Dockerfile .
- docker build -t i3sessnet/is2-mysql -f db.Dockerfile .
```

Results at https://travis-ci.org/I3S-ESSnet/is2

### Dockerhub
Docker also offer a free service for open source prosjects. We have set up automatic building of images on Dockerhub https://cloud.docker.com/u/i3sessnet/
