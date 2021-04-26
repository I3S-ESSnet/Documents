# Report on lessons learned
WP 3 has as overall objectives provide a blueprint og implementating the blueprint to be able to establish and build a sandbox environment and test available services in a containerized enviroment. The environment has been used to perform functional tests of services (see WP 1), and validate their packaging and installation. 

Methods and technologies for containerization has been studied and guidelines (D3.1.1. - Blueprint) and resources (D3.1.2. - Implementing the blueprint) has been delivered. The blueprint document provides an overall description for establishing a runtime environment for implementing modern sharable services following the CSPA standards and principles as containers. Within the document we have described the concepts, guidelines and considerations for providing and developing services, as well describing some considerations related to security and logging. Implementing the blueprint provides examples on implementations using the concept of "Infrastructure as code" as well as how to implement sharable services on these platforms. 

In the following sections of this document we will discuss some of the identified challenges related to establishing an enviroment for implementation of sharable services, and also give examples of success. 

Even though there has been challenges and obstacles in the process we do think that we have met the objectives as described in the project description. The collaboration with WP 1 and WP 2 has been important, both for binding the overall architecture descriptions to the technical architecture description in the blueprint og implementing the blueprint as well as the collaboration (discussions and deployathons) as proof-of-concepts and improvement of the processes to provide a platform for implementing shared services.

## Document and implement blueprint
Documenting and managing architecture in an environment where innovation and technology is constantly changing and evolving challenges the way we describe and document architecture and perform architectual design. From the initiation of the I3S project towards the end of this project we have experienced that defining the "sandbox platform" beforehand would limit the boundaries and innovation for implementing services on the platform. It would also result in an outdated blueprint by the end of the project. However, the overall international concepts, strategies and frameworks for NSIs have been used to describe and document important elements when establishing a cloud platform for shared services. The document is interconnected with the work of WP 2 describing the architectural guidelins and cookbook and the WP 3 deliverable implmentation of the blueprint as a proof-of-concept. From the planning of the project to finalise the deliveries the blueprint has to some extent changed in relation to granularity, which means that it does not document and describe technology artefact but focus on technology concepts and strategic approaches to consider.

The implementation of blueprint is a volatile document that serves as a proof-of-concept and guideline for establishing a platform in the cloud and implement shared services. One of the key successes for the deliveries in WP3 has been the collaboration with WP2 related to the blueprint both for agreeing on the content of deliverables but also to interconnect the architectural guidelines with the blueprint. Another success have been the deployathons and hackatons with members from the other work packages, these gatherings had an agile approach with highly skilled members to perform proof-of-concepts of shared services based on the concepts and descriptions in the blueprint. 

Our main purpose of implementing the blueprint has been to implement a platform with the capability of establishing shared services. Through the deployathons we have gathered experience and proven the ability to establish shared services on the platform. 

Implementing the blueprint has been focusing on the technical aspects of establishing the platform and shared services, we have not been able to work on the governance, management and security issues related to establish and manage cloud platforms for sharing services across NSIs. Sharing common platforms across organizations would require the capabilites to govern, manage and secure collaboration platforms for keeping up with the emerging technological change to reduce risks. The implementation of blueprint provides guidelines and examples for NSIs to establish platforms and services for sharing, that would not need to have governance bodies to handle collaboration between national borders. 

## Experience with implementation of blueprint and deployathons
- "Agile approach", not sufficient to apply guidelines and requirements. Agile and team approach.
- Containerisation of services and applications - Windows containers
  - Some legacy applications require running on Windows operating system. Docker supports Windows containers so there is not really a problem. But when you give it a try you soon discover how large the containers are. Just building a .NET 4.x application require a 10GB SDK image. The image for running the applicaton inside an IIS (internet information server) is 6.8GB. This means building av deploying windows applicatons take longer time than thypical Linux containers and the lightweight experience you expect with containers are missing. The Windows containers also require Windows host so just running an image to test an application will not work on other operating systems. 

  - We also testet managed Kubernetes on Azure (AKS) in 2020. Kubernetes clusters with  Windows worker nodes are supported but some features are still in preview as of 2021.

- Security issues
  - Next step: would have been securing applications and services using platform capabilities ...

## Concluding remarks
To keep track over two years (projects). Important elements when started the project has changed over time. Fail fast, change.

Other existing artefacts related to the blueprint.

IT architecture evolve in agile enviroment and organizations; the concepts, frames and strategies (autonomy and value boundary)

Physical meetings vs virtual meetings and deployathons. 

Sharing strategies - different expectations and requirements for governance, management and security
- Sharing platform
- Sharing services and applications
- Sharing code (infrastructure as code, services and applications)



