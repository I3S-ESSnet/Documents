# Paris meeting - 14-16 January 2021

The meeting was virtual and organized in three mornings from 13 to 15 January 2021. See also the [meeting agenda](agenda.md).

## Kick-Off session

The tracks leaders give an overview of the content of Track 1 (development of test services) and track 2 (service reuse).

### Track 1 description

The architecture recommandations have the following structure:
* The why?: a section focusing on the business drivers
* The what?: "we want to be metadata driven"
* The how?

The Cookbook is divided in two parts: the first on ARC and Relais, the second on schoolbook examples.

The schoolbook examples are managed and described in a [dedicated repository](https://github.com/I3S-ESSnet/ExampleServices).

During the track, we will work on the schoolbook scenario 1. The two services to be created are CAWI and Error Location.

### Track 2 description

Discussions will be about service reuse. Istat and Insee will present their work on their reuse cases. There could also be a presentation on the PXWeb reuse case.

The discussion will also be about the WP1 deliverables.

## Track 1

Repository where to find the code: https://github.com/I3S-ESSnet/ExampleServices

Presentation of the services to implement: https://miro.com/app/board/o9J_lbXK-AY=/

CAWI service:
* a web-based tool for surveys
* in .Net 3.1 (.Net React template, very simple off the shelf example)

Error localisation service:
* based on rules and a code list which will be a third service
* CAWI service makes REST requests on Error Localisation service

At the starting point, the code list (list of countries) is hard coded in the two services. Example of the hard coded questionnaire: EU Weather. 

The goal is to create a CodeList service and make changes to CAWI and Error Localization so they use the REST CodeList service.

Marco and Trygve worked on the Error Localisation service in Java, Romain and Benoît on the CodeList Service in Python, and Patrick and Jon on the CAWI in .NetCore.

More specifications are needed if we want to communicate about the results. It is also necessary to be able to run the services on one computer and to create Docker images to make a demonstration more easily.

## Track 2

The following reuse cases are reviewed:
* The **PXweb** reuse case is interesting, in particular regarding the organizational impact of open-sourcing on the PXweb community, but the report has to be completed.
* Regarding the **ARC** reuse case, Manuel demonstrates the now seamless inclusion of ARC in the I2S workbench; Istat confirms that ARC is perceived as a very interesting tool.
* As for the **Relais** reuse case, Insee presents the reuse report which still needs to be fleshed out; an addditional reuse case envisioned by Insee is discussed during a short videoconference with subject-matter experts.

Franck also gave an update on the developments concerning VTL tools:
* Eurostat has launched the open sourcing of the VTL editor that they are developing under the EUPL license.

* Good progress has been made on the [Trevas](https://github.com/InseeFr/Trevas) VTL engine. A video on Trevas can be found here: http://krmes.info/videos/Trevas-demo.mkv. Trevas is now working with [Apache Spark](https://spark.apache.org/), and work is ongoing to deploy it on a Kubernetes cluster.

Thanks to the "deployathon" sessions, it has been possible to gain experience on deploying services on a public cloud like [GCP](https://cloud.google.com/storage). To do it properly, you have to be completely in an "Infrastructure as code" logic, and for this you need different competences from those needed for pre-cloud resources.

## Consortium meeting

### WP1

Good results have been obtained, only some documentation is missing. It is necessary to improve the reuse report deliverables for the three services, and to update the documentation about ARC, Relais and perhaps PXweb. For this the user manuals will be used. Every deliverable will be published on the Sygma and CROS portals. For each service, the as-is and will-be architecture will be documented. It would be interesting to link the WP1 deliverables with the WP2 work. Over the next few weeks, Istat will organize dedicated meetings for each reuse case in order to finalize all deliverables.

### WP2

Currently, there is a very tight resource situation in Sweden. Some work remain to be done on the "why?". On the "what?" and "how?" chapters, it is necessary to merge specific aspects with WP3. The last deliverable is not very detailed in the grant, so what has to be done is not very clear. It is decided to go got a "low profile" document compiling elements from the different presentations done during the course of the project.

### WP3

The technical part has been done, a first version of the platform is available. The documentation (blueprint) has to be completed. There are two parts in this documentation: guidance on high level principles, and documentation on exploitation (in this part, the technologies change very quickly and it is difficult to have an up-to-date document: there could be a lot of appendices).

### WP4

The communication package is almost done. Some materials are work in progress: the video for ARC from France, PXweb testimony from Norway, and testimony for Tau-argus from Portugal.

The PXweb video is pending with the dissemination department, they have agreed to do it but it is necessary to find the time frame. The ARC video is planned to be done for the end of January.

The flyers have to be updated because they were intended for a physical meeting, not for virtual meetings.

### WP5

The changes made in the budget and the state of the deliverables have been presented.

### Deliverables and next steps

Actions for all WP leaders: 
* D5.1.5 Intermediary report 2, October 2020: each WP leader to update the draft report (sent by mail) before the end of January
* D5.5 Monitoring report 4, January: each WP leader to fill in the January monthly reports
 
Actions for WP1 leader:
* D1.2.2 Report on reuse of Service 1 (May): contact Manu to complete the document
* D1.3.2 Report on reuse of Service 2 (May): contact Istat to complete the document
* D1.4.2 Report on reuse of Service 3 (May): contact Rune to complete the document
* Send draft reuse reports for review by end of February
* D1.5 Guidelines on best practices (May): send a draft version before the end of January
 
Actions for WP2 leader:
* D2.1 Software and integration architecture recommendations (May): send draft version before the end of February
* D2.2 Cookbook on integration & use (May): send draft version before the end of February
* D2.3.1 Interactive report/guidance with examples (May)
* D2.3.2 Presentation on services and integration methods (May): 2.3.1 and 2.3.2 are very similar, aim at something simple for D2.3.2
 
Actions for WP3 leader:
* D3.1.1 Blueprint for the platform, including technology stack (March): the documentation (guidance, high level principles, exploitation documentation)
* D3.1.2 Cloud platform implementing the blueprint (April): make a delivery slip as for the service deliverables
* D3.3 Report on lessons learned (May): send a draft version before the end of February
 
Actions for WP4 leader:
* D4.1 Communication package on how to move to a service based architecture (May): will contain the survey, with the main elements about the results (cf. UNECE presentation) and the Sinder transformed into a specification for the CSPA catalogue. Send a draft version before the end of February.
* D4.2 Success stories (May): ARC and PXWeb videos to be provided
* D4.3 Lisbon Workshop (May): possible roadmap
  * publish [on GitHub](https://github.com/I3S-ESSnet/Documents/blob/master/lisbon-workshop/agenda.md) the agenda decided during the Paris workshop
  * give deadline to session chairmen for providing the introductory presentation of each afternoon
  * describe the organisation of the discussion groups (managers, statistician and architects, developers)
  * find who will make the two special topic presentations
  * determine the list of people to whom we send the invitation for the Workshop
  * send the invitation in February
  * book the webconference sessions


### NTTS presentation

Jakob will make the wrapping with his interactive presentation. We have to determine in which session we are and then decide which points we want to communicate. The topic could be "Track H. Frameworks, software and tools" (see NTTS program : https://www.conference-service.com/NTTS2021/documents/NTTS%202021%20topics_final.pdf)

It is proposed to make a short video on the success stories (for example integration of ARC and Relais) and a second video more GUI oriented ("this is how it looks like", a demo like video, like the one Nicolas Laval recorded for VTL tools).

What messages do we want to give about sharing services:
* possible? impossible? complicated?
* it has become practical, it is becoming more reality, it is the promise of CSPA.
* tell the story, we were there, and then CSPA, and now we are here...
* a great achievement is that IS2 is an implementation of GSIM
* go through the different results of the ESSNet
* end with questions about sustainability, in order to raise interests in people beyond the ESSNet
* it is possible because of open source

Franck, Mauro and Jakob will collaborate in preparing the presentation, Pedro will be the reviewer.


## Day 3

### Deployment session

Reproducing the method for deploying IS2 and ARC, the services developed during the workshop have been successfully deployed. Some difficulties were encountered, they will be documented.

## Lisbon workshop

Miro dashboard : https://miro.com/app/board/o9J_lb4VPS0=/

Physical or digital ?
* if physical, 3 days:
  * First morning: consortium meeting. First afternoon: whole presentation of the results of the project + special topics
  * Second morning: topic on statistical services. Second afternoon: architecture
  * Third morning: cloud and containers. Third afternoon: communication.
* if digital: one morning and three afternoons

Considering the pandemic situation, it is decided to make a virtual workshop:
* First morning: consortium meeting. First afternoon: whole presentation of the results of the project + special topic: "Fostering the cooperation"
* Second afternoon: topic on architecture, an introductory presentation and then discussion groups + special topic: "Service integration (VTL ...)"
* Third afternoon: joint topic on Services and Cloud, an introductory presentation then discussion groups

Possible roadmap for organizing the workshop:
* publish [on GitHub](https://github.com/I3S-ESSnet/Documents/blob/master/lisbon-workshop/agenda.md) the agenda decided during the Paris workshop
* give deadline to session chairmen for providing the introductory presentation of each afternoon
* describe the organisation of the discussion groups (managers, statistician and architects, developers)
* find who will make the two special topic presentations
* determine the list of people to whom we send the invitation for the Workshop
* send the invitation in February
* book the webconference sessions

## Conclusion


* Lot of work done, now we have to concentrate on documentation and deliverables
* Work on service reuse report (Istat pilot)
* Work on the Services Cookbook (Sweden pilot)
* Preparation of NTTS (Jakob, Mauro & Franck, Pedro reviewer)
* Lisbon: it will be virtual, the agenda has be adapted (consortium meeting; results of the ESSNet; two sessions on Architecture then Services and Cloud, each with discussion groups by profiles)
* Questions on the after-project
* We agree on our mains takeways:
  * Reusing services works concretely (the plug and play promise)
  * Open source forster collaboration for development and deployment
* Lots of questions on what strategy to adopt to push these ideas
  * top down: lobby ESS governance (mainly DIME-ITDG)
  * bottom up: set up communities, bi-/multi-lateral MOUs
* Have to liaise back with the MOS
  * "Sharing tools" activity stopped
  * Propose a new activity, or project for 2022?
