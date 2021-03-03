# Blueprint for I3S

## Background
Based on the work done in WP2, and using modern application architecture patterns we want to create a blueprint for a reference runtime environment for modern, sharable services following CSPA standards/principles using containers. It will not give any guidance on how to develop shared services, but will focus on the runtime environment for the services. This work package will describe the basic infrastructure needed, and implement a cloud instance for the needs of the ESSnet. The infrastructure will be documented as code, which will give to its users the opportunity to version it, and fork it. Typical products implementing this pattern would be Ansible Playbook or Terraform. Using the “infrastructure as a code” model will enable NSIs to easily create their own modern infrastructure on their premises. There will also be provided, as part of this WP a simple container-based platform using a cloud infrastructure, which will allow to validate the blueprint and to perform functional tests on the services developed in WP1, as well as validate their packaging and installation.

Retro-fitted, and modularized existing services will also be tested on the platform,either on premise or on the public cloud instance. This work package will also explore security components like IAM (Identity and Access Management), OAuth 2.0 and OPA (Open Policy Agent) for authentication and authorization, or Service Mesh for routing and secure service-to-service communication, for authentication and authorization. The WP will also look into how this type of security components can be added to existing services. Containerization and orchestration technologies, including Kubernetes and Docker, will be the basis of the platform, and all other infrastructure components will be built with it or around it.

![I3S - WP3 - Structure deliverables - Skisse til konseptuell modell for blueprint](https://user-images.githubusercontent.com/47101258/109776463-e3e2c300-7c02-11eb-952a-67516a033e8e.jpg)

### Why we need a different infrastructure platform
Traditional infrastructure is rigid, costly and not suited for supporting the rapid change in technology. Even with the advent of virtualization, and the ability to run hyper convergent infrastructure on premise, we tend to hit struggle with high complexity of our infrastructure, and high management cost of infrastructure. With high complexity, managing adequate security is also an issue. Containers hide some of this complexity, especially when it comes ot managing softare compatibility between software project, and cloud help us manage underlying infrastructure complexity by using managed infrastructure that can scale depending on the need of the organization.

## Containerization
There are several container initiatives, but the one that has been there longest, and have the largest adoption is Docker.  The container format is being standardized as part of the OCI (Open Container Initiative). Containerization is basically a way of creating a small virtual computer, that contains only the virtualized hardware required for the application you want to run, so it works as a way of transporting services without your application having to know anything about the environment around it. This is also its greatest challenge. In WP2 there will be described a lot of architectural guidelines for how you should design your application to make it scalable, and secure, so this document will only reference that work. A container is basically a virtual machine, but with as little or as much as you need to be able to run your application.

### Prerequisite
For starting to build services that you want to containerize, you will need a machine that can run Docker as a minimum, or a virtual machine that runs docker. There are also several online options for running containerized services. They greatly vary in price and functionality but can be used as a test for running simple services in the cloud (or on premise).

In general it’s hard to establish and maintain an on-premise, container platform from scratch, depending on your organizations maturity. But there are several good on premise platform-products that will help you with things like security and hardware provisioning, like Apache Mesos, and RedHat OpenShift.

## Environment
You can run Docker either on a Windows machine, or a Linux/Mac. Even .Net applications in containers are moving towards running on Linux host-systems (from .Net Core), so for minimal pain, you should set up your docker environment on a Linux machine, or in a virtual machine running Linux. 

We provide pre-designed virtual environments which have Docker pre-installed which can be used to set up your environment
On premise

For test purposes it should be sufficient to use a standard Docker installation for getting things up and running. For production quality runtime environments for containers and for container orchestration we recommend looking into products like Apache Mesos or RedHat OpenShift.

## Cloud
* Google Cloud Kubernetes
* Azure Kubernetes Service
* Amazon EC2, Amason EKS.

There is a plethora of other services that will ease the use of these public cloud vendors, like Pivotal's CloudFoundry, which will give you "serverless" functionality that can run on any of the large public cloud vendors. 

## Overall security
The description provides a brief documentation with an overview of relevant concepts to support a security modell for establishing services in a cloud environment. The documentation is based on the description of the security model in Statistics Norway (SSB Developer Guide) and documentation of deliverables in WP1, WP2 and WP3 in I3S. 

### Zero Trust
Zero Trust, Zero Trust Network, or Zero Trust Architecture refer to security concepts and threat model that no longer assumes that actors, systems or services operating from within the security perimeter should be automatically trusted, and instead must verify anything and everything trying to connect to its systems before granting access.

Service mesh is often considered as an important infrastructure component for facilitating Zero Trust in a micro service architecture.

References:
- [What is a Zero Trust Architecture?](https://www.infradata.com/resources/what-is-a-zero-trust-architecture/)
- [BeyondProd](https://cloud.google.com/security/beyondprod)
- [BeyondCorp](https://cloud.google.com/beyondcorp)
- [BeyondTrust](https://www.beyondtrust.com/blog/entry/why-zero-trust-is-an-unrealistic-security-model)

### Service Mesh
In software architecture, a service mesh is a dedicated infrastructure layer for facilitating service-to-service communications between micro services, often using a sidecar proxy.

Having such a dedicated communication layer can provide a number of benefits, such as providing observability into communications, providing secure connections, or automating retries and backoff for failed requests.

References:
- [Service mesh](https://en.wikipedia.org/wiki/Service_mesh)
- [What is Istio?](https://istio.io/latest/docs/concepts/what-is-istio/)

### User administration and authentication
Authentication is the process of verifying a users identity.

*Azure AD is used as the identity provider for SSB users. Users and groups are managed in an on prem AD and synchronized to Azure AD. Keycloak is used for providing OAuth 2 and OIDC support to applications running in Google Kubernetes Engine (GKE). Read more about authentication in BIP in the Authentication services documentation.*

### Authorization
Role-based access control (RBAC) is a method of restricting access to data and operations a user can perform based on the users role in the Organization.

Access control in applications running in BIP should be implemented using a role based access control system. But it is possible that Attribute based access control (ABAC) is used to some extent, especially when it comes to data ownership.

### Logging and Monitoring
Logging is important in any security model for auditing and forensics.

Log scraping should be done for alle Applications. It is especially important that access related information is logged by applications to assist with auditing.

References:
- [OWASP Logging Guide](https://owasp.org/www-pdf-archive/OWASP_Logging_Guide.pdf)
- [Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)

### Automated Configuration Management
The role of automated configuration management is to maintain systems in a desired state in order to reduce cost, complexity and errors. This is especially important in a Zero Trust architecture where configuration transparency, traceability and consistency in a system is essential for security.

Terraform, Ansible and declarative manifests for describing system and application state and GIT for change management and traceability is often used.

### Managing secrets
Secrets like passwords, certificates and keys are probably the hardest assets to manage in any system, but also the most important asset. Leaked keys can lead to unauthorized access to sensitive data and have severe consequences for the organizations trust, reputation and reliability.

Examples of tools is Secret Manager, Berglas and Sealed secrets. 



## Considerations

...

