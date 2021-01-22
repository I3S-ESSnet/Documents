# Paris meeting - 14-16 January 2021

## Kick-Off session

### Track 1 description

Architecture recommandations structure :
* 1st, the why : a section focusing on the business drivers
* 2nd, the what : "we want to be metadata driven"
* 3rd, the how

The cookbook is divided in 2 parts : 1st on ARC and Relais, 2nd on schoolbook examples.

Schoolbook examples :
* Scenario 1 : starting point and goal, the goal is the starting point for the scenario 2
* The goal of scenario 2 is context aware
* For scenario 3, once again the goal of scenario 2 is the starting point. Scenario 3 implements a new feature which is event driven.
* In scenario 4 we want to implement the contenairisation feature.

During the track, we will work on the schoolbook scenario 1. The two services to be created are CAWI and Error Location.

### Track 2 description

Discussions will be about services reuse. Istat will present their work on their reuse case. There could also be a presentation on the PXWeb reuse case.

The discussion will also be about the WP1 deliverables.

## Track 1

Repository where to find the code: https://github.com/I3S-ESSnet/ExampleServices

Presentation of the services to implement: https://miro.com/app/board/o9J_lbXK-AY=/

CAWI service:
* web based tool for surveys
* in .Net 3.1 (.Net React template, very simple off the shef example)

Error localisation service:
* based on rules and a codelist which will be a third service
* CAWI service makes Rest requests on Error Localisation service

At the starting point, the code list (countries) is hard coded in the two services. Example of the hard coded questionnaire: EU Weather. 

Goal : create a Codelist service and make changes to CAWI and Error Localization to use the REST CodeList service.

Marco and Trygve worked on the Error Localisation service, in  java, Romain and Benoît on the Codelist Service in Python, and Patrick and Jon on CAWI in .NetCore.

More specifications are needed if we want to communicate about the results. It is also necessary to be able to run the services on one computer and to create Docker images to make easily a demonstration.

## Track 2

3 reuse cases :
* The **PXWeb** reuse case is interesting but too general, it has to be precised.
* **ARC** reuse case, demonstration of ARC in I2S workbench
* Meeting with Insee colleagues who want to reuse **Relais** at Insee

Eurostat will opensource the VTL editor they are developing, the aimed licence is EUPL.

Lot of progress has been made on the Trevas VTL engine. A video on Trevas can be found here: http://krmes.info/videos/Trevas-demo.mkv. It is now working with Spark, it is planned to deploy it on a kubernetes cluster.

Thanks to the deployathon, it has been possible to gain experience on deploying on a public Cloud like (GCP), to do it properly you have to be completely in an Infra as code logic, and for this you need different competences from those needed for pre-cloud resources.

## Consortium meeting

### WP1

Good results have been obtained, it is only missing some documentation. It is needed to improve the reuse deliverables for the 3 services, to update the documentation about ARC, Relais and perhaps PXWeb. For this the user manuals will be used. Every deliverable will be published on the Sygma and CROS portals. For each service, the as-is and the will-be architecture will be documented. It would be interesting to link the WP1 deliverables with the WP2 work.

### WP2

Currently, there is a very tight resource situation in Sweden. Some work remain to be done on the why. On the what and how chapters it is necessary to merge specific things with WP3. The last deliverable is not very detailed in the grant, so what has to be done is not very clear.

### WP3

The technical part has been done, a first version of the platform is available. The documentation has to be finished, it is the blueprint, something exists but has to be completed. There are 2 parts in this documentation : guidances on high level principles, exploiting documentation (in this
part the technologies change very quickly, it is difficult to have an up to date document, there could be a lot of appendices).

### WP4

The communication package is almost done. Some materials are work in progress: the video for ARC from France, PXWeb testimony from Norway,
and testimony for Tau-argus from Portugal.

The PXWeb video is pending with the dissemination department, they have agreed to do it, necessity to find the time frame. The ARC video is planned to be done for the end of the January (see with the internal communication team).

The flyers have to be updated because they were intended for a physical meeting, not for virtual meetings.

### WP5

The changes made in the budget have been presented.

### NTTS presentation

Jakob will make the wrapping with his interactive presentation. We have to determine in which session we are and then decide which points we want to communicate. The topic could be "Track H. Frameworks, software and tools" (see NTTS program : https://www.conference-service.com/NTTS2021/documents/NTTS%202021%20topics_final.pdf)

It is proposed to make a short video on the success stories (for example integration of ARC and Relais) and a second video more GUI oriented ("this is how it looks like", a demo like video, like the one Nicolas Laval recorded for VTL tools).

What messages do we want to give about sharing services :
* possible ? impossible ? complicated ?
* it has become practical, it is becoming more reality, it is the promise of CSPA.
* tell the story, we were there, and then CSPA, and now we are here ...
* a great achievement is that IS2 is an implementation of GSIM
* go through the different results of the ESSNet
* end with questions about sustainability, in order to raise interests in people beyond the ESSNet
* it is possible because of opensource

Franck, Mauro and Jakob will collaborate in preparing the presentation, Pedro will be the reader.


