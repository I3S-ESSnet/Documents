# I3S ESSnet Toulouse hackathon minutes


## Monday 13 January: consortium meeting

The morning begins with a welcome by the Toulouse Regional Director. Then the main points of the agenda are reviewed :

Monday - consortium meeting
  * Welcome and introduction
  * Update on the work done in each WP
  * Agenda and organization of the week
    * Objectives of the hackathon
    * Presentation of the technical tracks and constitution of the groups
    * Content and organization of the "Intermezzo" session

Tuesday, Wednesday morning, and Thursday - technical tracks
  * Architecture
  * Development
  * Communication

Wednesday afternoon - intermezzo ideas
  * articulation of I3S work and Unece standards (CSPA, CSDA, GSIM, GAMSO…)
  * fill the CSPA catalogue for I3S services
  * presentation on notebooks (Norway)
  * paper for Q2020 (Benoît)
  * feedback on the most recent deliverables
  * specification of delivery slips for software deliverables
  * demonstration of VTL developments

Friday - conclusion
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

**Track 2: Development**

  * ARC/IS2 integration (resume work on data model, build the interface to the database)
  * VTL tools
  * PXWeb cloud deployment (and also with ARC/IS2)

**Track 3: Communication**
