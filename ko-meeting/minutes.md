# I3S kick-off meeting

## Minutes

### Tour de table and expectations

Many of the expectations are shared by all the participants in the ESSNet. The project is seen as an opportunity to go forward
in sharing services and an enabler in a context where it is not easy to obtain resources. For those who have not
been part of the first ESSNet, this KO meeting is a good start point to have more information.
The focus put on the architectural aspects and the building of a container platform is appreciated.
Along with the technical questions, the organisational aspects are mentioned:
* how does it work in real life ?
* what can be released in the CSPA catalogue ?
* how to discuss with non-IT people ?
* how to support services after integration ?

### ESSNet Presentation

The I3S (Integrating Shared Statistical Services) ESSNet is following the SCFE ESSnet. Like this
first part, the objectives of the ESSNet are to foster the reuse of statistical services
among the National Statistical Institutes. This secnd part focus more particularly on new services
and technical implementation.

Questions and remarks:
* There is a schedule for the reuse of the service, is reuse in production an explicit goal ? Eurostat answer:
no, it is different from SCFE1, containerizing is important but not exactly linked with developing new services.
* Reusing is also a question of documentatin, organisation... containerization can lower the barrier of deployment in IT system
* SCFE has shown that most of the time was used because of organisational aspects
* tghe ESSNet will have to provide guidelines on how to implement a shared service
* WP4 should provide success stories and not so successful stories. Real stories provide much experience on what are the main difficulties.
* The catalogue is not yet an appstore, we have not already a lot of experience in putting services in the catalogue. With more experiments will come more feedbacks.

### WP1 presentation

The objectives of this WP are to develop and reuse 3 to 5 new services from the list established in the ESSnet SCFE, with the selection criteria being:
* Select services from the “Top 10” services referenced in the CROS portal document
* The project has an objective to cover GSBPM level 1 processes. Therefore, selected
services should apply those criteria.

The list of possible services is:
1. Record linking
2. Microdata access (confidentiality on the fly)
3. Content data validation
4. Error correction
5. Questionnaire design
6. Outlier detection
7. Bulk mailer
8. Named-entity recognition
9. Generalized data loader
10. DataSetCatalog
11. PX-Web

Questions and remarks:
* Ror evaluation each DO will have to evaluate its own development regarding the 3 A dimensions, and ROs will evaluate at least 3 services for reuse.
* The methodology developed in WP4 of SCFE1 has been put in a EU Survey, now it is usable by everybody.
* Some services in the list are costly to reuse, or even not possible to reuse. Some could be merged (for example: Data loader and Content validation).
* How to know the desire for the services ? It has been evaluated for some during SCFE1, it is the first A dimension (Attractivity)
* If the service has already an implementation in the CSPA catalogue, it can't be chosen another time for another implementation because it brings nothing in GSBPM coverage.

### WP2 presentation

This work package will study, explore and describe the different architecture possibilities for integrating services (e.g. orchestration, publish/subscribe, point-to-point, adapters, containers). NSI have different as-is situations and different goals that the to-be architecture should align with. A list of real life examples in NSIs where the situation and goals differs will be selected and guidance will be provided to show the effect of choosing different integration patterns. Examples of goals that the architecture should align with could be stronger data and metadata governance or agile production processes. These examples should be the foundation of the architectural discussion.

Other features that are expected in real situations are for instance capabilities for:
- Logging
- Containerization
- Authorisation
- Status monitoring
- Service scaling

Questions and remarks:
* the architectural pattern could be a good starting point. What was developed in the architectural pattern Working Group was very theoretical, I3S is a good opportuity to test the patterns
* WP3 looks a lot like a blueprint for WP2. There is a lot of things from WP3 wich could enrich WP2.

### WP3 presentation

Based on the work done in WP2, and using modern application architecture patterns we want to create a blueprint for a reference runtime environment for modern, shareable services following CSPA standards and principles using containers. This work package will describe the basic infrastructure needed, and implement a cloud instance for the needs of the ESSnet. The infrastructure will be documented as code, which will give to its users the opportunity to version it, and fork it. Typical products implementing this pattern would be Ansible Playbook or Terraform. Using the “infrastructure as a code” model will enable NSIs to easily create their own modern infrastructure on their premises. There will also be provided, as part of this WP a simple container-based platform using a cloud infrastructure, which will allow to validate the blueprint and to perform functional tests on the services developed in WP1, as well as validate their packaging and installation. Retro-fitted, and modularized existing services will also be tested on the platform, either on premise or on the public cloud instance.

### WP4 presentation

Based on the work in other work packages, and gathering information from other NSIs member of the ESS, this WP will aim at building stories of successful use and reuse of CSPA services, building on others' experience and lessons learnt to foster further and wider adoptions in the ESS. It will present these stories and other results through different means in different existing fora of the ESS (e.g. working groups, task forces, workshops) and organise its own meeting. Different tools will be used to create or present the stories, amongst which surveys and interviews.

Questions and remarks:
* The goal of the communication is to communicate on success stories. To start we should share about what we consider
a success story, to deliver the message to whom, what kind of newsletter...
* A metodology for this WP could be: 1. what is a success story, or a real story ? 2. to focus on which aspects of implementing services ? 3. format : newsletter, hackathon, videos
* LOS ESSNet, hacktahon PLOSH, articles in Digicom Newsletter could be taken as examples
* A hacktahon for WP4 ? In order to work on communication kits, make videos, for example interviewing non IT people (DG ...)
* Good candidates for WP4: jDemetra+, Eno, questionaire from WP4 SCFE
* We could have a visual identity
* WARNING: make the distinction between WP4 and WP5

### WP5 presentation

The aim of Work Package 5 is mainly to make sure that the project meets its expectations in terms of schedule and outputs, and to oversee the communication activities in relation with the other work packages, and in particular with Work Package 4. During the two years of the project, meetings and videoconferences will be organised where the ongoing tasks, deliverables and open questions will be discussed between the project members.

### Second day: selecting reusable services

**Discussion:**

* Many services are almost achievable, but the costs are very different
* Not a lot of NSIs in the ESSNet, we could make a last check with the community before validation
* Some services are complementary, there is an architecture question to cope with
* Wish to have more time (or ressources) in the project because many services are interesting; difficult to justify the assessment we are trying to do.
* The ressources are different for each country, so achievability and affordability are different for each country
* Analogy with Monopoly strategies in order to define our strategy
* What should be the first chosen service, the most or the less mature ? And the last chosen service, the less mature ?
* If budget is a constraint, choose affordability
* If we plan to adapt budget, choose achievability
* Insee is working on ARC, Istat is working on Outlier detection, Statistics Sweden is working on PX-Web
* Named Entity Recongnition is high in attractiveness, but not in achievability. In 6 month the situation and the cost will be clearer.
* How do we define success ? is it to deploy in production ?
* There could be also implementations outside of this group. During the workshop in June, it will be possible to discuss with other countries
* There can be some money from SDMX - VTL, but it will be on individual ground


**Final results**

| Service | Order | DOs | ROs |
|---|:-:|:-:|:-:|
| PX-web | 1 | SCB | INE (draft), SSB (final) |
| ARC | 2 | Insee (and SSB for VTL) | Istat |
| Record linking | 3 | Istat | Insee |

**The winners**

![Services selected](wp1/services-selected.jpg)

**The glorious contenders**

![Services not selected](wp1/services-not-selected.jpg)


### Next steps

**Work package 1**

| What? | Who? | When? | Notes |
|---|:-:|:-:|:-:|
| **Global**|
| Set up a timeline and list of tasks | Every service subproject | As soon as possible | A clear set of milestones |
| Plan collaboration meetings | Every service subproject | By the end of Feb |  |
| Small reports on progress | Every service subproject | |  |
| Common framework of reusing | WP leaders |  | |
|||||
| **PX Web** |
|Learn about current version and perform quick assessment of requirements|INE|March||
|Test the current version (on a Windows platform)|INE|End of March||
|Implementation project on adapting PX-WEB in the existing environment |INE|April||
|Updating to .NET Core based on internal analysis |SCB|Not before summer|Further assessment is needed on internal planning of resources|
|Set up the platform for build and test (including containerization)|SCB|September|Link to WP3|
| **ARC** |
|Document the current architecture and capabilities|Insee|End of February||
|Define the TO-BE Architecture in line with I3S principles|Insee|End of March||
|||||
| **RELAIS** |
|Transfer of knowledge from the current Relais team and the team that will handle the development during the ESSNet |ISTAT|End of March||
|Proposal for a TO-BE Architecture and new implementation of RELAIS service|ISTAT|End of May||
|Plan the development phases|ISTAT|End of May||
|Start the development|ISTAT|June||

**Work package 2**

* Planning in detail (end feb/start of mars)  VC (Jakob check with Taeke)
* Setup google-drive documents and share plus share prezi
* Setup the general structure of the documents
* During hackathon in Rome
	* Share guidance-document if applicable
	* Monitor the development services
	* Try to capture scenarios during the sprint for the cookbook
		* Translate the scenarios to the cookbook and create interactive guidance in prezi plus video
* In May deliver draft of cookbook
* Test the current output during modernstats world workshop
* Deliver draft of arch guidance (july)
* Between july and december - add guidance and scenarios based on experience and the work done in WP1 and WP3
* Align deliverables and deliver draft versions in dec 2019
* Setup indicators for the test in M13
* M13 - test the deliverables using developers and architects that are not part of the work and get feedback (making use of environment from WP3)
* M14 Align WP2 deliverables with all other WPs 
* M13-M18 continued work on adding guidance, cookbook scenarios and interactive guidance
* M18 Align deliverables and deliver Drafts
* M19 Perform second test on deliverables 


**Work package 3**

| What? | Who? | When? | Notes |
|---|:-:|:-:|:-:|
|Create a simple VirtualBox with Docker, Docker compose and build-tools for the hackathon | SSB, INSEE (Frédéric), Romain | M6 | |
| Howto guide, using the Virtual machine.  | Norway, Insee (Frédéric), Romain, Sweden | M6 | How we should do development: Git, Build chains, etc |


**Work package 4**

| What? | Who? | When? | Notes |
|---|:-:|:-:|:-:|
| Success story of reuse of PX-web | INE | April |  |
| Success story on cookbook | SCB/INE/Insee | December |  |
| Success story on open software development | INE/Insee | December |  |
| Success story on co-development of PX-web | INE/SCB/SSB | February 2020 |  |

Ideas of success stories:
  - JDmetra (methodology, re-use, center of excellence)
  - tau-Argus / mu-Argus
  - co-development Istat / Insee
  - working stories on reuse cases (ex: INE reuse of PX-web in April)
  - test phases of WP2
  - post-analysis of a reuse case that worked
  - testimonies of end users or participants to ESSnet project, or associated colleagues
  - report on "service market" in MSW workshop
  - post-mortem analysis of an example of failure?


Future success stories: sustainability

**Work package 5**

| What? | Who? | When? | Notes |
|---|:-:|:-:|:-:|
| Monitoring report | Insee | April |  |
| Prepare MSW workshop |  |  |  |
| Consortium VC |  |  | Use Unece WebEx? |
