# WP3 - Build a sandbox and test available services - containerize

> Insert initial description
> This draft is probably to long, consider content in chapter 3.1.1. However, chapter 3.2 would probably not be long.

The deliverables in WP3 has proven the ability to establish shared statistical services as containers in a cloud infrastructure. Using the blueprint and implementing the blueprint NSIs should be able to implement shared services in their own ecosystem as well. 

## Task 3-1: Sandbox platform
The main goal for this task was to describe a blueprint for å sandbox environment and implement a cloud platform as infrastructure as code. These deliveries should serve as a foundation for the service containerization deliveries in Task 3-2. 

### D3.1.1 - Blueprint for the platform
The blueprint document produced covers the following issues: 
* Background, including the rationale for establishing an infrastructure platform, capabilities of such a platform and how it is linked to WP2: Define integration and architecture guidelines.
* Providing services describes the base capabilities and considerations for establishing a cloud platform, including scaling, containerization, environment and cloud.
* Developing services discusses the reasoning for open source and licensing as well as considerations and principles to consider for collaboration and sharing of services.
* Overall security and logging describe some concepts and patterns for handling security and logging. 

Delivery 3.1.2 demonstrates how the infrastructure is documented as code to enable NSIs to create their own modern infrastructure. Together with the deliveries in Task 3-2: Service containerization it shows the implementation of a container-based platform using cloud infrastructure as "Shared Statistical Services" following CSPA standards and principles. 

The work is based on the workshops in the Rome hackathon (May 2019), in these workshops we brainstormed and identified capabilities, technologies and services needed for establishing a platform. Among others based on the CSPA features like scalability, security and sandboxing needed to implement shared statistical services using cloud technologies. This work formed the basis for the first draft of the blueprint and implementing the blueprint. The Toulouse hackathon (January 2020) and the tracks related to architecture discussions and scoping of the architecture guidance and cookbook delivered by WP2 formed a base for the development and scoping of the blueprint documentation for WP3. In between these two physical hackathons Statistics Norway and Statistics Sweden met to discuss the relation and scoping of WP3 and WP2. 

Documenting the blueprint changed during the project to less emphasis on technologies and more on concepts and patterns to consider when establishing a cloud platform. The reason for this was to reduce the risk of delivering a blueprint in which was outdated when the project is finished. As the innovation and technology is constantly changing and evolving the focus on concepts, patterns and considerations should give users the foundation for implementing platforms and containerizing services. For further readings on lessons learned and experiences with the delivery of WP3 see also [Report on lessons learned](https://ec.europa.eu/eurostat/cros/system/files/i3s_-_d3-3_final.pdf).

### D3.1.2 - Cloud platform implementing the blueprint
Implementing the blueprint document is a guideline for how the project has implemented the platform and the containerization of services. "Infrastructure as code" is part of the delivery and enables NSIs to establish their own infrastructure in their own ecosystem. 

The document produces covers the following issues: 
* Containers: Application containerization, Docker compose, CI and examples
* Platform deployathons: Building a platform, deploying services, packaging
* PXWeb on Azure
* Try the GCP platform yourself (as a step by step guide to create a Google cloud project and a service account)

Both the Toulouse and Rome hackathons served as important meetings for the delivery to implementing the blueprint, in addition we arranged several deployathons in the autumn of 2020 in which developers met and solved technical issues related to the implementation of the platform and the shared statistical services. Some technical issues and the how we experienced the collaboration between WPs in containerizing services is documented in [Report on lessons learned](https://ec.europa.eu/eurostat/cros/system/files/i3s_-_d3-3_final.pdf) and the platform deployathon chapter of the document [Cloud platform implementing the Blueprint](https://ec.europa.eu/eurostat/cros/system/files/i3s_-_d3-1-2_final.pdf).

## Task 3-2: Service containerization

> Description on service containerization (keywords: Platform capabilites as foundation, support in containerization of services etc) eventually refer to other relevant documents 

* D3.2.1 - Package container for Service 1 (ARC)
* D3.2.2 - Package container for Service 2 (PXWeb)
* D3.2.3 - Package container for Service 3 (Relais)

## Task 3.3: Reporting
This delivery is a report on lessons learned based on the work and deliveries in Task 3.1 and 3.2 as well as the relation to deliveries in WP1 and WP2. This delivery discusses the process and how the deliveries has evolved, collaboration with deliveries in the other WPs. In the conclusions of the lessons learned we emphasize the importance and needs related to security issues as well as governance and management of shared cloud platforms. For further readings [Report on lessons learned](https://ec.europa.eu/eurostat/cros/system/files/i3s_-_d3-3_final.pdf)
