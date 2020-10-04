# Oslo meeting - minutes

## WP5 presentation

### Deliverables

* It is necessary to resubmit D1.2.1 (ARC Service) because things have evolved since the last submission.
* D2.1: the final version is planned for M24, but the last months will be necessary to really finalize it. Same situation for the Cookbook. The communication deliverable will be more like a draft by the end of the year.
* D3.1.1 (blueprint): it is currently a draft, some elements have been delivered on github (part documentation, part code). Now final is planned for M28, but it will be a good thing to begin to deploy the services before M27.
* D1.5 (Guidelines and best practise): it is necessary to have a discussion around the document in order to move forward (during this hackathon and the next one). There is a possible overlap with other deliverables (especially the deliverable on architecture). It is intended to focus the guidelines on the experience and practise of integrating and reusing.

### Budget

* The staff cost for Sweden is around 100%. A transfer from other parts of the budget is proposed.
* Subcontracting: Insee (security audits for ARC, Relais and PXWeb ; for Relais and PXWeb it is necessary to tell Insee when the code is stable), Istat
(Relais is a little bit monolithic, the idea of the subcontracting is to break Relais in smaller pieces, then subcontracting is about Relais architecture. Not all the budget will be used), Norway (most of the money is still not used, plan to use it for the Google platform)

### Communication actions

In the near future, there are 2 conferences:
* NTTS, the deadline for abstract is in november.
* ModernStat Workshop, the deadline for abstract is in september.

### Other topics

Will the next hackathon be multi-located ? Yes, it is a possibility.

## Lisbon workshop

The objective is to invite beyond the ESS, but there is the question of the budget. The UNECE was willing to help with the budget for inviting people if it is a CSPA event. It is necessary to check that this offer is always on the table. The ESSNet on its own doesn't have the budget for inviting 50 people. We can plan to invite some influencers, the others will have to pay for their participation.

Due to the pandemic situtation we must think about different solutions for the organisation and have a B plan: physical meeting, virtual, mixed meeting, physical and virtual, streaming of the presentation, having chat...

We plan to have a 2.5 or 3 days meeting, so we need very interactive sessions (technical and non technical).
* 1st half day (monday 26/4 morning): consortium meeting with Eurostat about the results of the ESSNet and planning for the future
* 2nd half day: presentation of the results of the ESSNet to the audience of the workshop, lessons learnt and open points
* 1-1.5 days of mixed presentations and interactive sessions
* last half day: a service market and contributions for people coming from outside the consortium

Ideas of presentation/interactive sessions:
* a discussion on the requirements that make it easier to reuse a service or implement sharable services or put it in practise
* interactive session on the survey
* architecture with an interactive session
* session on reuses
* Sinder
* bring your own data in PXWeb or Relais
* bring your own app in the platform

## PXWeb presentation

Objectives:
* publish PX-Web as a shared service
* adapt it to open standards such as .NET Core and HTML5
* contenairize it

PX-Web fulfils the following CSPA features:
F1. Documentation
F2. Internationalization
F6. Security solutions
F8. Sandboxing for exploration(Demo)

In the near future the following CSPA features will be implemented:
F3. Open Source
F9. Containerization

Work done so far:
* Version 2020 v1 Maj 2020 OpenSource & containerized.
* PX.Plattform upgraded to .Net Standard
* PXWebComparer - The testing application.
* PX.Web-API presentation layer not done.

Roadmap:
* PX.Web-API (presentationlayer) moved to beginning of 2021
* PX.Web Nextgen Planned to start after summer 2020 is moved to summer 2021
* Next PX.Web 2020 v2 planed release date dec 2020 (WCAG)

Reuse of PXWeb: cf. https://github.com/I3S-ESSnet/Documents/blob/master/wp3/pxweb-reuse.md

Main lessons learned from reuse: the collaboration allows not to create everything from scratch, the feedbacks about the database structure.

A video on PXWeb will be made by the communication department of the Norway institute. INE and INSEE will send the questions for the interview.

## Architecture

https://docs.google.com/document/d/1V154mfO4pkOXuNOljZeN2V80DoxmtZnTvA-Q3UO2Y6o/edit

The document is considered to be at the good level for architects who have to discuss with the managers. So, it will be interesting to have more feedbacks from managers about it. It is suggested to focus more on costs in order to make understand the interest of sharing. The document may be used in many ways, it can be seen online or used for a presentation in a workshop, it could be filmed ... it is the main idea of this deliverable.

## ARC

Presentation at : https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/H1t_OfXXP#/

The ESSNet core engine version is now the same as the INSEE ARC core engine production version. The deployment of the ARC ESSNet version in INSEE production is planned for the end of the year. ARC is more and more reused in INSEE. ESSNET helps a lot for that as it gives more visibility to the applications involved in the project. I3S helps ARC to enhance the quality, the performance and the documentation of the application. These are important points for the business decision makers.

ARC REST webservices to execute ARC modules have been developped in August. These webservices were needed for an internal ARC reuse case for the Insee project SIRENE4. This will also allow to finalize the ARC-IS2 integration for November. A further step will be to test the data and workflow sharing between ARC and Relais.

An ARC Tutorial has been written after the 16/06 virtual hackathon to present the ARC concepts and how to proceed with simple csv files : https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/rJzPiJp3U

Questions and remarks :
* What is the link between ARC and IS2 ? It will be a good thing to have a standalone ARC for heavy production, but it will also be a good thing to have ARC integrated into IS2 in order to be used directly by statistical expert. We can see that there arer two business cases here.
* Adding functionality in IS2 is currently a beta feature. Istat wants to have a roadmap for finalizing this functionality by the end of the ESSNet.
* Have some efforts been made for configuring the database and choose the database engine (other than Postgresql for example) ? Not yet, an objective for ARC was to be able to load huge amounts of data, so the use of database is very optimized and specific to PostgreSQL. If it is needed to use another database engine or to load another kind of data sources, it will require a lot of developments.

### Reuse case

Reuse test with the "Division for acquisition of administrative data and integration of sources" at Istat. Two administrative sources have been used on the collect and check input phases. The process has been redesigned according to the ARC model.

### Communication

* A flyer is almost finished.
* A video will be made on the cooperation ARC-Relais (Manuel Soulier and somebody from Istat). INE and Insee will propose a list questions for the interview.

## Interview on multi-organization open source collaboration

National strategies:
* Norway: all the written code is on github, opensource softwares are used as much as possible. There are huge problems with vendor lockers. Proprietary Clouds could cause the same situation. How should we approach opensource development in a community like I3S ? How the code should be created ? A liberal licence is chosen in order not to be a problem for the people using the code. The NSI is using opensource softwares, is developing opensource softwares and creating a community around this developments. Creating opensource increases the quality of the code. A policy is defined, licences have been chosen. The most difficult point is the community.
* Sweden: for the softwares used internally, there is no strategy about opensource but things are changing. The statistics on the site are always opensource (in CCBy). For the developped softwares, it is a case by case choice. There are different stages of maturity in the staff. IT people are quite familiar with the concepts, but are struggling with the practical questions (who is responsible for the core, for fixing bugs ...). Regarding developing opensource softwares, there is mainly PXWeb.
* Istat: there were a lot of lockings with vendors. Istat policy is not to publish all developped software in opensource, but for example, in project like I3S the strategy is to publish everything in opensource. No corporate github account, each developer has its own. It is thanks to project such as I3S that IStat use more and more collaborative tools. Globally, the maturity level is quite low, it depends on the skills of the staff. Istat started to put the code on github, but there are many different repositories. At the management level, there is not a good awareness of the subject, no process has been defined for producing opensource. Like in Sweden, there are problems with practical questions.
* Insee: a few years ago, Insee began to publish opensource software. But the organisation was decided bottom-up. Now things are changing, a strategy on the organisation is beginning to be defined. Insee is not at the first level of maturity, perhaps at the second one.

Summary of the level of maturity :
* Level 1: Istat
* Level 2: Sweden and France
* Level 3: Norway

A parenthesis on compliance: the Linagora mission will have a look at the code and provide recommandation regarding the property state ; for the users compliance is mainly a question of copyright respect and licences compatibility ; for the producers, compliance is mainly a question of copyright respect (respect of the contributions of the developers).

In order to make an auto-evaluation you have to answer these questions: 
* what is your perception of your maturity ?
* do you have any private venture partners who reuse the code, whith whom do you share the code ?
* do you have subcontractors for developing the code ?

Subcontracting:
* Norway: there are consultants who write code, StatNorway has the ownership of the code, the consultants have to produce opensouce code. There are some projects with other entities, but these projects don't produce opensource because of the partners.
* Sweden: same situation as Norway.
* Istat: there are subcontractors, Istat owns of the code. The NSI has to be cautious, because sometimes the code remains the property of the company and only the finished product is owned by Istat. No partners, but there are some projects with entities like agencies wich are interested in the services of Istat.

Linagora question: let's say you all agree to let eurostat lead your co-innovation community, would you all agree to transfer your intellectual property rights in a non-exclusive way to Eurostat ? In order to allow Eurostat to have the same rights as you on the code ?
It is not easy for NSIs to give the answer to this question.

Next steps: summarize the interviews, analyse the code to see if there is compliance actions to undertake. If there is compliance breaches, a first estimation of the worload to correct them will be given. A scenario for a general organisation will be also delivered.

## VTL presentation

Presentation at : https://github.com/I3S-ESSnet/Documents/blob/master/oslo-meeting/vtl-tools.md

### Reuse
* Is it the first implementation of VTL for the logic of a questionnaire ? Probably yes, but for now it is a simple one. There was a first description of a questionnaire logic, before VTL was available, but it used an adhoc language.
* We have to find a way to organize the adoption of VTL in the ESS community, this requires the possibility to give feedbacks on the language.
* How to handle the version of the VTL code ? For now, we don't. There is a development by Eurostat for this functionality.

All partners agree on adding VTL Tools to the scope of I3S.

### Communication
* At least a flyer
* a tutorial for the developers (for the users: a tutorial on the language is on the scope of Eurostat). Istat will be beta user abd codeveloper of a tutorial on Trevas.

## Year-end Hackathon

Possible subjects:
* the work on architecture, the cookbook and the examples (part of the architecture work)
* finish the deliverables
* to precise what we want to achieve with the Lisbon workshop
* ARC-Relais integration
* the platform (including deployment)

Duration: 5 days ?

Where: at Istat, all travels and seminaires are cancelled until the end of the year, it is more or less the same in every country.

## Relais

Work done:
* porting to PostgreSQL
* internationalization: now in italian and english
* data load: possible to load data from both files and databases
* test reports, quality reports, docker images
* performance improved, more than 50% faster

Work in progress:
* currently both probabilistic and deterministic approaches in the software, the process has been splitted in steps
* service functionalities: creation of search space, batch process, quality indicators for assessment of record linkage process
* bugs fixing
* improvement of the performance of the record linkage algorithms (Java parallel stream, Apache Spark)

Next steps:
* documentation: update of architectural documentation, new user guide, tutorial
* modular architecture: new client with VueJs, Spring cloud data flow
* improvement of ARC and RELAIS integration

### Reuse

https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/H19sdPG7w#/

INSEE choosed RELAIS to redesign the linkage process of the BPE application. This application builds an important database for INSEE called "Permanent facilities database" (BPE). The Permanent facilities database is used to track and keep up to date what community facilities which are available on the french territory for a given year. The concept of community facilities is broad and data must be collected each year from several data providers.

BPE use linkage for data consolidation. The BPE statisticians use the BPE application to finalize the integration of the files of the year in the BPE database. To do so, the BPE application proceed and report the result of a linkage between the new year datafile and the previous year datafile. The goal of this linkage is to know what facilities must be kept, deleted or created.

The actual BPE linkage requires 3 specific variables with determined name and concept (idsource as facility identifier, typequ: type of facility, adresse1 as the facility location). As a consequence, the statisticians have to rework each of input files to create the required variable with the right name and content. The others variables of the files which could give extra information on the linkage cannot be used. The algorithm is not suitable for all of the provided datasources as sometimes, a variable is missing or other most valuable variables cannot be used.

The statisticians are aware of the BPE linkage limits and feel that using RELAIS is a good opportunity to enhance the BPE linkage and the quality of the final database. A preliminary study document had been written in september 2019. A proof of concept to reuse RELAIS for BPE linkage has started on march 2020. Most of the technical problems had been exposed at the “16 June 2020: Istat-Insee mini-hackathon” and cleared shortly after.

The work of evaluating the RELAIS record linkage (the probabilistic and the deterministic one) is in progress. The evaluation of the statistician workflow should occur at the end of 2020 and the use case tested still must be defined.

## Service deployment

Work done:
* routines for containerization
* provisioning of infrastructure using Terraform
* establish project on Azure
* establish project on Google Cloud Platform
* work on Terraform is still in progress

Next steps:
* formalizing the infrastructure for MS Azure and GCP
* Complementing WP2 documentation
* What type of workflow is necessary for a cloud native platform ?
* a study and a blueprint using GitOps
* Strategy and techniques: canary deployment, secret handling

WP3 challenges:
* organization of code and documentation
* things are constantly evolving, the addition of GitOps is a useful addition
* Billing and IAM

Discussion:
* what is delivered in WP2 is just a draft regarding the service mesh, it is important to have a focus on ease of use or on documentation
* first provide blueprint (develop it more around high-level principles, not specific technologies because things are constantly evolving)
* Question interesting reusers: When and how can I install my application on the platform ? Right now it depends, there are several ways of doing the deployment, a first way is simply using the docker image and deploy it, but the idea is to provide more tools and services for deployment
* we have to decide what is exactly the deliverable for the platform
* there is two goals in WP3, we want to have a platform for the ESSNet and we want to provide other institutes a blueprint of what could be a platform. Is there also a third goal: a more permanent offer for the ESS, what happens on the 21st of May 2021 ? Do we shut down the platform or do we offer a platform for the ESS ?

## NTTS

https://ec.europa.eu/eurostat/cros/content/ntts-conferences_en
Deadline for abstracts: 15th of october
Tracks: softwares, frameworks and tools, specific topic: reusing tools and services

It is not possible to have a specific session. We have to make individual contributions. It is necessary to organize a meeting next week in order to discuss what we want to submit.

## Modernstat world workshop

https://statswiki.unece.org/display/MWW2/ModernStats+World+Virtual+Workshop+2020

Ideas of presentations:
* Communication, during "the new development" session, about the principles of the communication (Pedro, Insee)
* Architecture (Jakob)
* Relais-ARC
* Service deployment

Abstract for the 10th of September.

Can we make the same contributions for NTTS ?

## Other next steps

There will be an intermediary meeting in october (duration: 2 hours).

## Actions plan

 * All
   * Finalize next hackathon organisation
   * Lisbon Workshop: ideas for interactive session
   * Input for the UNECE Workshop

 * Sweden
   * D2.1 (Guidelines) and Cookbook, final in M24.
   * Communication deliverable, draft in M24

 * Norway
   * Deploy the services on the platform before M27
   * Determine exactly how much money is needed for GCP
   * Make a video on PXWeb with the questions provided by WP4
   * Organize a deployathon

 * Italy
   * D1.5: guidelines and best practise, organize a discussion to move forward
   * Complete documentation on Relais
   * Make Relais architecture evolve (client with VueJS, Spring cloud data flow)
   * Improvement of ARC and Relais integration

 * France and Italy
   * Make a tutorial for the developers on VTL
   * Make a video on ARC

 * France
   * Security audits
   * Finish the flyer on ARC
   * Organize the october meeting

 * France and Portugal
   * Send a list of questions to Norway for the video on PXWeb
   * Make a flyer on VTL
   * Send a list of questions to France for the video on ARC

 * Linagora
   * Linagora summarize the interviews on " multi-organisation opensource "
   * Analyse the code, provides a general organisation scenario
