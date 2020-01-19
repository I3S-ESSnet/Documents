# I3S ESSnet Toulouse hackathon minutes


## Monday 13 January: consortium meeting

The morning begins with a welcome by the Toulouse Regional Director. Then the main points of the agenda are reviewed :

**Monday - consortium meeting**
  * Welcome and introduction
  * Update on the work done in each WP
  * Agenda and organization of the week
    * Objectives of the hackathon
    * Presentation of the technical tracks and constitution of the groups
    * Content and organization of the "Intermezzo" session

**Tuesday, Wednesday morning, and Thursday - technical tracks**
  * Architecture
  * Development
  * Communication

**Wednesday afternoon - intermezzo ideas**
  * articulation of I3S work and Unece standards (CSPA, CSDA, GSIM, GAMSO…) (Pina)
  * fill the CSPA catalogue for I3S services (Pedro)
  * paper for Q2020 (Benoît)
  * feedbacks on the most recent deliverables (D1.1, D2.1 and D2.2; Mauro and Jakob)
  * specification of delivery slips for software deliverables (Pierre)
  * demonstration of VTL developments (Hadrien and Nicolas)
  * presentation on notebooks (Trygve)

**Friday - conclusion**
  * Reports from the technical tracks
  * Next steps
  * Finalization of intermediary report
  * Next hackathon
  * Roadmap

### WP1

Questions/remarks :
  * The objective of the WP is finally to reuse, that is also a deliverable of the WP.
  * Each collect service has its own data model, the dissemination service has to disseminate to different clients in different formats, but in the middle the analysis service needs to have an unique model / format (subject for WP2)
  * The discussion on the guidelines on best practices will take place on Wednesday
  * Deliverables : first service (ARC) has been delivered (discussion on the format to come), the containerisation au the second service has been delivered (PxWeb in Windows implementation)
  * What about PXWeb ? The code is here (and opensource; tests need to be delivered) but there is no delivery slip for it. The use case has to be defined.
  * What is the exact name of the deliverable ? The number in Sygma is only for Eurostat, the name on CROS is the right name.


### WP2

Questions/remarks :
  * The D2.2 (Cookbook) has the more overlap with the blueprint work, should we separate more theses 2 deliverables or merge the two deliverables ?
  * D2.3 will feed WP4, and could be reused for example in UNECE works.
  * The 4 layers in "What" could be linked with Domain Driven Design.
  * Proposition to have a hackathon, at least 2 days, on the example services (where are implemented the features).
  * What is the target audience for the video ? Not only in the ESS, can be more open (but not for the statistics offworld), the target should be the CSPA community.


### WP3

Questions/remarks :
  * If you use a provider, lock you into it. This locking question has to be adressed. Notice that Google App Engine allows you to deploy plain containers. At CBS, there is a move toward Cloud Foundry, supposed to be provider independant (CBS contribution welcome on the subject).
  * Question of the Database : in the container ? Database of the provider ?
  * CI and automatic reporting is a plus for transparence and confidence. In general, it is a good thing to have everything open (bad example : opensource but on a repository not visible for people without identifier and password)


### WP4

Questions/remarks :
  * We should have a feedback on the survey in the next DIME/ITDG meeting.
  * The catalogue should adress some problems, mainly the problem of promoting the existing services. Should the catalogue be enriched with something more personal (video ...).
  * There is a need to explain what are the standards and what they mean.
  * The lack of knowledge about services is surprising and raises the question of how we communicate in the CSPA community. That's why we think the messages should be different for different targets.
  * Propose to have a special section on sharing services during NTTS ?

### WP5

Questions/remarks :


### Presentation of the tracks

**Track 1: Architecture**

Arcitecture guidance, cookbook and interactive guidance. Discussion on the scope, the structure, the content and the overlap between WP2 and WP3.

Participants: Jelger, Jakob, Hendryk, Manu, Giusepina, Trygve.

**Track 2: Development**

  * ARC/IS2 integration (resume work on data model, build the interface to the database)
  * VTL tools (operators, date and time, refactoring and naming, documentation, design for non scalar operators)
  * PXWeb cloud deployment (and also with ARC/IS2)

Participants: Vincent, Rune, Patrik, Romain, Mauro, Franck, Hadrien

**Track 3: Communication**

  * Finalize jDemetra+ flyer
  * Start ARC flyer and video script
  * Finalize Relais flyer
  * Start PxWeb flyer
  * Finalize the Guildelines on success stories"
  * Analyse survey first results - start sinder; complet communication kit; feedbacks to DIME-ITDG
  * Begin to discuss the workshop in Lisbon agenda

Participants: Pedro, Pierre, Hakim, Marco, Benoît

### Objectives of the hackathon

  * Draft deliverables reingeneering
  * Feedbacks on the Relais wrokbench
  * Database integration into the cloud
  * CSPA implementation in architecture (WP2) documents
  * Feedbacks on WP2 contents (and good level of details)
  * Ideas on cookbook
  * Platforms running
  * Stable version of the VTL tools
  * Diagrams to put in WP2 document
  * Enough information in order to make promotion at CBS
  * How to contribute
  * See something real, tangible
  * Draft for the Sinder
  * Planning for the second part of the project
  * Agree on the boundaries between WP2 and WP3
  * Have two services able to talk to each others
  * Intermediary report, minutes ...

## Intermezzi

### Frameworks

  * links between the standards, links between the deliverables of the ESSNet
  * GSIM very important for modeling the statistical processes and define standard processes
  * CSPA has a collection of principles, the other standards are frameworks. CSPA is more best practices and guidances, the other standards are more normative.
  * The architecture guidelines delivered by the ESSNet must apply the CSPA principles, they also must consider the different GSBPM phasis and on lower level you have to refer to GSIM objects. It is how all the standards can be used in practical application.
  * Architecture guidelines are more on a conceptual level, the Cookbook and the Blueprint are more on a physical and technical level.
  * Then it is possible to talk of the lessons learnt in the real implementation of the standards.
  * Future of CSPA. The next step is to have it endorsed by the CES (amongst all the UNECE standards as a all)
  * GSIM is currently too detailed to be easily implemented, it should be simplified.
  * The discussion has also covered the topic of feedbacks on deliverables
  * The description of the architecture is rather static, work on the dynamic aspects should be done (roles).

### CSPA Catalogue

  * Hindrance for sharing and reusing: some countries don't know what is available for sharing
  * Proposition to enhance the content of the Catalogue
  * The owner of a service can modify it in the Catalogue. I3S could create/improve the information for Relais and PXWeb (and ARC ?)
  * A country which reuses a service can click in the Catalogue in ordre to declare it.

### Format of the delivery slip

  * There needs to be snapshots
  * Use labels in the github repository. Possible for the source code. For the containers, we can publish the dockerfiles and tag them.

### Demonstation of VTL tool

**Introduction and Use case**

  * Specifying questions requires some script language (logic flow, variables)
  * Example of a question [specification](http://pogues.scfe.eu/rmspogfo/#/questionnaire/k07w61mf) and [rendering](http://stromae.scfe.eu/rmesstromae/fr/esa-dc-2018/questionna/new?unite-enquete=123456789):
  * Example of [complex questionnaire](http://pogues.scfe.eu/rmspogfo/#/questionnaire/simpsons) with controls.
  * Controls are currently specified in a custom XPath-like language that we want to replace by VTL. We need:
    * JavaScript VTL editor to include in Pogues for the specification of controls
    * A JavaScript VTL interpretor for the rendering next generation of CAPI questionnaires
  * For the transition:
    * Eno needs to translate XPath controls into VTL for Lunatic
    * We might need to translate from VTL to XPath for the current XFomrs platform

**VTL Tools in JavaScript**

  * Leverage on components generated from the formal grammar by Antlr
  * Open source on Insee's [GitHub repository](https://github.com/InseeFr/VTL-Tools)
  * Integration pipeline with [Travis-CI](https://travis-ci.org/InseeFr/VTL-Tools) and [Coveralls](https://coveralls.io/github/InseeFr/VTL-Tools)
  * Inclusion of VTL in the [Lunatic editor](https://inseefr.github.io/Lunatic/editor)
  * The interpretor: [Functional coverage](https://inseefr.github.io/VTL-Tools/en/coverage.html)

## Tracks reports

### Architecture track

### Dev track

### Com track

**Proposition for a flyer template** (with propositions of questions in order to help filling the different parts):
  * Header with logo, and possibly the receiver (What is the name of the service ? Who is the source of the service ?)
  * Service description: history (How long has it been used ? Is it used in other NSIs ? What have been the incentives to develop and use this service ?), functionalities (Which problem is solved ?), architecture (Is it possible to relate to the GSBPM ?)
  * Conditions of using
  * Documentation and additional resources, link to the Catalogue (What is the channel to obtain the service ? Is a manual available ? Is there any help desk ? What is the level of technical support ? Is there any support for day to day operation ? Is there some tool/demo app to evaluate/try the service ?)
  * Future development
  * License
  * Contact (Does the possibility to provide feedbacks on the service exist ? Is there a user group ? Is it possible to contribute to the development of the service ?)

**Discussion on the Sinde:**
  * Will it be a Catalogue app ? It can be an enhancement of the filters, for example to also propose a more user-friendly application
  * The first question is the GSBPM phases or subprocess, the first choice could presented as an image of the GSBPM
  * criterias in the Catalogue: license type is important (proprietary, free but proprietary, opensource "not viral", opensource "viral")
  * in the Sinder we only show tool with "final" in status and "implementation" in type of document
  * technology criteria: java/dotNet/JS/R/other
  * for methodology, it is difficult to build a decision tree in order to precise what is searched for, perhaps could we just propose standard/non standard ?
  * allow people to add questions in the Catalogue so that these questions can be used by the Sinder ?


**First try for Lisbon agenda:**

first day morning (9:00 to 12:30):
  * results of the ESSNet (all the morning)

first day afternoon "Beyond the ESSNet" (14:00 to 17:30):
  * icebreaker (30 minutes)
  * lessons learnt and open points in the ESSNet (and the survey) (30 minutes)
  * additional questions (and the answers) for the survey, not in plenary but in small groups (1 hour)
  * coffee break
  * restitutions in plenary (15 minutes)
    
second day morning "CSPA session":
  * presentation of CSPA 2.0 (30 minutes)
  * the catalogue (30 minutes)
  * the Sinder (30 minutes)
  * coffee break
  * VTL presentation (1 hour)
  
second day afternoon "Practical session":
  * Contenairisation for the dummies
  * "I build my statistical process with the services in the Caatalogue", in small groups


Other ideas for the Lisbon workshop:
  * session on architecture ?
  * presentation of the awesome list by CBS, what do you do with that ?
  * opensource strategy of NSIs ?
  * a practical session on the IS2 Workbench
  * target audience : managers ? developers ? architects ? In Wiesbaden the audience was very mixed, we could do the same
in Lisbon
  * "more than contenairisation for dummies": "cloud for dummies"
  * presentations by services owners and users

## Hackathon results and next steps

**Objectives:**
  * Draft deliverables reingeneering ==> Done
  * Feedbacks on the Relais wrokbench ==> Done
  * Database integration into the cloud ==> Done
  * CSPA implementation in architecture (WP2) documents ==> Done
  * Feedbacks on WP2 contents (and good level of details) ==> Done
  * Ideas on cookbook ==> Still pending
  * Platforms running ==> Done
  * Stable version of the VTL tools ==> Still pending
  * Diagrams to put in WP2 document ==> Done
  * Enough information in order to make promotion at CBS ==> Done
  * How to contribute ==> Done
  * See something real, tangible ==> Done
  * Draft for the Sinder ==> Done
  * Planning for the second part of the project ==> Done
  * Agree on the boundaries between WP2 and WP3 ==> Done
  * Have two services able to talk to each others ==> Still pending
  * Intermediary report, minutes ... ==> Almost done


**Next steps:**
  * redo the delivery of service 1
  * redo the delivery of the contenairisation of service 1
  * do the delivery of service 2 (for the end of the month)
  * do the delivery of the contenairisation of service 2 (for the end of the month)
  * service 3 for March
  * reuse report template (resp.:Insee)
  * each reuse organisation begins write the reuse reports
  * for WP2, final versions are for M24
  * WP3: guidelines (draft) for M14
  * next virtual meeting: May or June
  * for WP1: a mini sprint in Roma on integration of Relais and ARC, and a subject on VTL

**Oslo meeting:**
  * official period is August
  * have the Lison Workshop in January 2021 ? Check with Eurostat and INE
  * ==> date of Oslo meeting: week of 31st of August 2020
  * invite Finland people (for the geospatial ESSNet) ==> an intermezzo ?
  * a kind of final meeting for I3S
  * focus on the reuse cases of the service
  * a track on the example service for the Cookbook
  * a track on finalising WP1
  * a track on preparing Lisbon
  * a track on the feedbacks on UNECE level

***UNECE feedbacks:*** link in the agenda
  * Insee contacts Taekke, and organises a videoconference with UNECE and WP2
  * discuss with the french representative in the SG DIME/ITDG how to communicate about the results of the ESSNet
  * if ideas about the Sharing Tools Group, send them to Jakob
