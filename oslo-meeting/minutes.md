# Oslo meeting - minutes

## WP5 presentation

### Deliverables

Resubmit D1.2.1, ARC Service because things have evolved since the last submission, and see with Pierre.

D2.1 : final version in M24, and last months to really finalize
also for Cookbook
for the communication deliverable, more a draft on M24

D3.1.1 : blueprint, it is a draft, sthg is on github, part documentation, part code, try the way to present the result in a proper way
now final is M28, but it will be a good thing to begin to deploy the services before M27

During Toulouse hackathon, Pierre Peyronnel was precise on what he wanted in the service deliverables

Deliverable 1.5, Guidelines and best practise, have a discussion around the document in order to move forward, during this hackathon, during the next one.
Possible overlaps with other deliverables (architecture).
Focusing the guideline on the experience and practise of integrating and reusing

### Budget

Staff cost ; Sweden around 100%

Subcontract :
#### Insee
==> security audits for ARC, Relais and PXWeb, for Relais and PXWeb tell Insee when the code will be stable
#### Istat
a consultant , Relais is a little bit monolithic, the idea of the subcontracting is to break Relais in smaller pieces (so for security audit : wait another few months), so subcontract is about Relais architecture. Not all the budget will be used (check how this budget can be reused)
#### Norway
most of the money is still not used, plan to use it for the Google platform

### Communication actions
What do we do for NTTS ? Deadline for abstract in november.
ModernStat Workshop, deadline in septembre.
Discussion at the end of the meeting.
Ohter ideas ? 

### Questions
For the next hackathon : multi-located ? yes, it is a possibility.

## Lisbon workshop

The objective is to invite beyond the ESS, but there is the question of the budget. The UNECE was willing to help with the budget for inviting people if it is a CSPA event. It is necessary to check that this offer is always on the table. The ESSNet on its own doesn't have the budget for inviting 50 people. We can plan to invite some influencers, the others will have to pay for their participation.

Due to the pandemic situtation we must think about different solutions for the organisation and have a B plan : physical meeting, virtual, mixed meeting : physical and virtual, streaming of the presentation, having chat.

We plan to have a 2.5 or 3 days meeting, so we need very interactive sessions (technical and non technical).
* 1st half day (monday 26/4 morning): consortium meeting with Eurostat about the results of the ESSNet and planning for the future
* 2nd half day: presentation of the results of the ESSNet to the audience of the workshop, lessons learnt and open points
* 1-1.5 days of mixed presentations and interactive sessions
* last half day: a service market and contributions for people coming from outside the consortium

Ideas of presentation/interacive sessions:
* a discussion on the requirements that make it easier to reuse a service or implement sharable services or put it in practise
* interactive session on the survey
* architecture with an interactive session
* session on reuses
* Sinder
* bring your own data in PXWeb or Relais
* bring your own app in the platform

## PXWeb presentation

Objectives :
* publish PX-Web as a shared service
* adapt it to open standards such as .NET Core and HTML5
* contenairize it

PX-WEb fulfills the CSPA features :
* F1. Documentation
* F2. Internationalization
....

V2020 : OpenSource
Summe 2020 : Web-API .Net Core

Questions :
* FC : the version of April 2021 will be the one delivered for the end of the ESSNet. Hakim : it will be the API on .NEt Core
* TF : how do this change the initial packaging ?
* Pina : the one officially use ? 2020 v1

Reuse of PXWeb :
cf. https://github.com/I3S-ESSnet/Documents/blob/master/wp3/pxweb-reuse.md

Pina : for all type of surveys or for specific ones ? For disseminating data

Main lesson learned from reuse : the collaboration that allows not to create everything from scratch, the feedbacks on the database structure

Video on PXWeb in Norway : ask the communication department, contact Pedro in order to have the questions for the interview (for next month), then have text available in order to make translations

## Architecture

https://docs.google.com/document/d/1V154mfO4pkOXuNOljZeN2V80DoxmtZnTvA-Q3UO2Y6o/edit


RT : for the management, focus more on cost, in order to make understand the interest of sharing

FC : it is at the good level for the management, could have more feedbakcs from manager. JE : the document is for architects who have to discuss with managers

RT : to be seen online, or to be used for a presentation in a workshop ? JE : many options, could be for a presentation, could be filmed, do it on your own and navigate and focus on what you want ==> it is the main idea of this deliverable, having online/remote workshops (==> also a possibility for an interactive session in Lisbon)

RT : link parts of the presentation to the document ? JE : absolutely

## ARC

Presentation at : https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/H1t_OfXXP#/

ESSNET core engine version is now the same as the INSEE ARC core engine production version. The deployment of the ARC essnet version in INSEE production is planned for the end of the year.

ARC is more and more reused in INSEE. ESSNET helps a lot for that as it gives more visibility to the applications involved in the project. I3S helps ARC to enhance the quality, the performance and the documentation of the application. These are important points for the business decision makers.

ARC REST webservices to execute ARC modules have been developped in august. These webservices were were the needer for an internal ARC reuse case for the Insee project SIRENE4. This will also allow to finalize the ARC-IS2 integration for november. A further step will be to test the data and workflow sharing between ARC and Relais.

An ARC Tutorial has been written after the 16/06 virtual hackathon to present the ARC concepts and how to proceed with simple csv files : https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/rJzPiJp3U

Questions and remarks :
* link between ARC and IS2 ? It will be a good thing to have a standalone ARC for heavy production, but it will also a good thing to have ARC intergated into IS2 in order to be used directly by statistical expert. We can see that there arer two business cases here.
* adding functionality in IS2 is currently a beta feature. Istat want to have a roadmap for fianlizing this functionalityt by the end of the EssNet.
* Have some effort been made for configuring the database and chosse the database engine (other than Postgresql for example) ? Not yet, an objective for ARC was to be able to load huge amounts of data, so the use of database is very optimized and sopecific to PostgreSQL. So if it is needed to use another database engine or to load another kind of data sources, it will require a lot of developments.

### Reuse case

Reuse test with the "Division for acquisition of administrative data and integration of sources" at Istat.
Two administrative sources have been used on the collect and check input phases. The process has been redesigned according to the ARC model.

## Interview on multi-organization open source collaboration

Norway strategy : all the code written is on github, use of opensrouce software as much as possible. Huge problem with vendor lockers from before, another is the use of proprietary Cloud. How we should approach opensrouce development in a community like I3S ? How the code should be created ? Choice of a liberal licence in order not to be a problem for the people using the code.

Sweden strategy : 3 parts. For softwares used internally, no strategy about opensource but things are changing. The statistics on the site are always opensource in CCBy. For the softwares developped : it is case by case.

Istat strategy : before a lot of lockings with vendors. Istat policy is not to publish all developped software in opensource, but for example, in project like I3S the strategy is to publish everything in opensource. No corporate github account, each developer has its own. It is thanks to project sucah as I3S that IStat use more and more collaborative tools.


Linagora question : what is the maturity level of your organisation on the question of opensoruce compliance ?

France : a few years ago, Insee began to publish opensource software. But the organisation was decided bottom-up, now things are changing, a strategy on the organisation is beginnign to be defined. Not first level of maturity, perhaps second one.

Norway : under ?%. Using os, creating os, creating a community about that. Creating opensource increase the quality of code. Pretty mature, policy in place, licences chosen, (? the difficult point is community)

Sweden : less mature than Norway, different stages of maturity in staff, IT people quite familiar with the concepts, struggling with the practical questions (who is responsible for the code, for fixing bugs ...). Code opensource : mainly PXWeb. When speaking about opendata, the institute is very mature, this is potential for opensource strategy.

IStat : maturity level is quite low, it depends on the skills of colleagues. Starting to put the code on github, but many different repository. Not a good awareness on the management level, no process defined for producing opensource. Like in Sweden, prbms with practical questions. Not yet in the mindset of the whole institute.

Summary : Istat ==> level 1, Sweden and France ==> level 2, Norway ==> level 3

A parenthesis on compliance. Content of the mission : have a look at the code and provide recommandation regarding the property state. For user part, compliance is mainly copyright respect and licences compatibility. As a producer, copyright respect (respect of the contributions of the developers). There is also the organisation, some don't allow opensource and even co-innovation licences.

A questionnaire for auto-evaluation : yes, the first question is about your perception of maturity, and then "do you allow us to evaluate your maturity". 2 more questions : "do you have any private venture partners who reuse the code, whith whom you share the code ?", "do you have subcontractors for developing the code ?"

Subcontract :
Norway : consultants who write code, ownership of the code to StatNorway, and the consultant have to produce opensouce code. Some projects with other entities, but don't have to produce opensource because of the partners
Sweden : not different from Norway.
Istat : subcontractors, so Istat owner of the code, have to be cuatious sometimes because the code remains teh property of the company and only the finished product is owned by Istat. No partners, but work with entities like agencies wich are interested in the service of Istat.

Linagora question : first idea of the role of each one of us in term of legalship, contribution to the roadmap ?
Trygve : this is a tricky part of opensource, the choice of the licence has an impact on the legal question. Question for the community : collaborate on an existing code or fork it ? The hard part is to decide a governance for the project.
Istat: the main pbm is the management of the project, the capacity to have people contributing for a long period.

Linagora : let's say you all agree to let eurostat lead your co-innovation community, would you all agree to transfer your intellectual property rights in a non-exclusive way to Eurostat ? In order to allow Eurostat with the same rights as you on the code ?
France and Istat : not sure it is possible.
Istat : in the case of IS2, the software has been created in the context of Eurostat (an ESSNet)
Sweden : not sure to understand the complexity of the subject. Linagora : the question is if all of us want to have Eurostat on the copyright.

Next steps : summarize the interviews and the same time analyse the code to see if there is compliance action to undertake. If there is compliance breaches, first estimation of the worload to correct will be given. A scenario for a general organisation will be also delivered.

## VTL presentation

Presentation at : https://github.com/I3S-ESSnet/Documents/blob/master/oslo-meeting/vtl-tools.md

### Reuse

Questions :
* Use VTL for questionnaire logic, is it the first implementation ? Probably a first yes (but for now, a simple one). In fact there was a first description of the questionnaire logic, before VTL was available, and it used an adhoc language.
* we have to find a way to organize the adoption of VTL in the ESS community, this requires the possibility to give feedbacks on the language
* How to handle the version of the VTL code ? For now, we don't. There is a development by Eurostat for this functionality.

TO add VTL Tool to scope : Norway ==> OK, Sweden ==> OK, Istat ==> OK

Communication
* At least a flyer
* a tutorial for the developers (for the users : tutorial on the language is the job of Eurostat) ==> Istat as beta users abd codevelopers of a tutorial on Trevas

## Discussion on various points.

Communication for ARC : a flyer is almost finished, a video will be made on the cooperation ARC-Relais (Manuel Soulier + quelqu'un d'Istat) ==> propose a list questions for the interview (4-5 minutes), see with Pedro

### Year-end Hackathon

subjects :
* to push on the work on architecture, the cookbook and the examples (part of the architecture work)
* finish the deliverables
* to precise what we want to achieve with the Lisbon workshop
* ARC-Relais integration
* the platform (including deployment)

organisation : an orevall linking framework based on the presentation of architecture

duration : 5 days ?

where : at Istat all travels and seminaires are cancelled until the end of the year, the same in every country ?

## Relais

Work done:
* porting to PostgreSAL
* internationalization : now italina and english
* data load : possible to load data from both file and database
* test reports, quality reports, docker images
* performance improved, more than 50% faster

Work in progress:
* currently both probabilistic and deterministic approaches in the software, the process has been splitted in steps
* service functionalities: creation of search space, batch process, quality indicators for assessment of record linkage process
* bugs fixing
* improvement of the performance of the record linkage algorithms (Java parallel stream, Apache Spark)

Next steps:
* documentation : update of architectural documentation, new user guide, tutorial
* modular architecture: new client with VueJs, Spring cloud data flow
* improvement of ARC and RELAIS integration

### Reuse

https://hackmd.io/@EgVaFRsUQ-ywTiFcXIsWig/H19sdPG7w#/

INSEE choosed RELAIS to redesign the linkage process of the BPE application. This application build a important database for INSEE called permanent facilities database (BPE). The permanent facilities database is used to track and keep up to date what community facilities are available on the french territory for a given year. The concept of community facilities is broad and data must be collected each year from several data providers.

BPE use linkage for data consolidation. The BPE statisticians use the BPE application to finalize the integration of the files of the year in the BPE database. To do so, the BPE application proceed and report the result of a linkage between the new year datafile and the previous year datafile. The goal of this linkage is to know what facilities must be kept, deleted of created.

The actual BPE linkage requires 3 specific variables with determined name and concept (idsource as facility identifier, typequ : type of facility, adresse1 as the facility location. As a consequence, the statisticians have to rework each of input files to create the required variable with the right name and content. The others variables of the files which could give extra information on the linkage cannot be used. The algorithm is not suitable for all of the provided datasources as sometimes, a variable is missing or other most valuable variables cannot be used.

The statisticians are aware of the BPE linkage limits and feel that using RELAIS is a good opportunity to enhance the BPE linkage and the quality of the final database. A preliminary study document had been written in september 2019. A proof of concept to reuse RELAIS for BPE linkage has started on march 2020. Most of the technical problems had been exposed at the “16 June 2020: Istat-Insee mini-hackathon” and cleared shortly after.

The work of evaluating the RELAIS record linkage (the probabilistic and the deterministic one) is in progress. The evaluation of the statistician workflow should occur at the end of 2020 and the use case tested still must be defined.

## NTTS

Deadline : 15th of october

contact the organisation team to discuss what is possible

H-track : softwares, frameworks and tools, specific topic : reusing tools and services

Can we have a specific session ?


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
* what is delivered in WP2 is just a draft regarding service mesh, so important more important to have a focus on ease of use or documentation
* first provide blueprint (develop it more around high-level principles, not specific technology because things are constantly evolving)
* Question reusersWhen and how can I install my application on the platform ? Right now it depends, several way of doing the deployment, first way simply using the docker image and deploy it, but the idea is to provide more tools and services for deployment
* we have to decide what is exactly the deliverable for the platform

