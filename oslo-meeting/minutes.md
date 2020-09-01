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

TO extend to more participants, who will pay ? 
The UNECE was willing to help with the budget for inviting people
if it is a CSPA event.
Jakob : is this offer always on the table ?

Romain : we need to be as large as possible ==> ESS and CSPA

Italy : invite the IT DG members ?

We don't have the budget for inviting 50 people
we can plan to invite some influencers, the others
will have to pay for their participation

A mixed meeting : physical and virtual ? streaming possible ?
having chat ?
Due to the high volatility of the situation, we need a B plan

==> 1. invite beyond the ESS

just to present the results
also continue on working together and planning for the future

Sweden : if we choose 3 days we need very interactive sessions

Italy : if the audience is really large, we can have different sessions
not only technical sessions

==> 2.5 days workshop
1st half day : consortium meeting and the result of the ESSNet
1 day of presentations
1 day of practical thing
half day for a service market and contributions for people coming from
outside the consortium
monday 26/4

******************

adding a discussion on the requirements that make it easier
to reuse a service or implement sharable services or put it
in practise

*********************************

2nd half day :
presentation of the results, general presentation, not the details
lessons learnt and open points
interactive session on the survey

2nd half day presentations :
details of the result of the project
1. architecture ==> with an interactive session
2. session on reuses
3. interactive sessions on ?
last. Sinder

bring your own data in PXWeb or Relais
bring your own app in the platform

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

