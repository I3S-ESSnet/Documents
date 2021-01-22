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

