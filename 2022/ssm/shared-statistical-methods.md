# Shared Statistical Methods

#### Background

Over the years, initiatives like __CSPA__ (UNECE), __ESSNet Serv2__, __ESSnet I3S__ have all tried to solve the problem of sharing statistical services across countries. Sharing is hard, and there are many hurdles to be crossed. Many of those hurdles are technical, organizational and cultural. 

One area that usually have a lot of focus is the area around _Statistical Methods_. These are being promoted f.ex. through _The awesome list_ (link), and are increasingly released to the public domain through various _Open Source_ licenses. 

The challenge is still that these _Statistical Methods_ some times lack the software craftmanship of other types of modern software. The methods themselves are from a methodology perspective of very high quality.  From a software perspective, things like non-functional requirements, portability, testability etc. are not always taken into account. CSPA 2.0 tried to lay out a path for adresseing some common software architectual issues surrounding services in general. 

![CSPA 2.0](cspa.png)

Some things have changed dramatically over the last 5-10 years though. The adoption of _Open Source_ in Statistical offices have increased. The willingess to share code have also increased, and with that a more open and collabarative environment. 

#### Statistical Methods

_Statistial Methods_ are in this document losely defined as a collection of algorithms expressed in software and used in a Statistical Production. [Citation needed.. :-)].

Software like JDMetra and TauArgus are great tools for Seasonal adjustment and Discloure Control and have been widely adopted. Both are Open Source, and especially JDMetra is greatly supported, and have a relativley active development community. TauArgus is being supported, but is lacking out-of-the-box multi-plattform support. 

Both software packages (and this is based on it's current releases) could be more modular, and have a greater split between user-interface and the actual service they provide. 

#### The problem

Some of the areas ESSNet I3S explored was the area around build automation and deployment of services. We need to be able to build and deploy the services that the production platform needs. To be able to serve statistical methods as services, we need them to be at a minimum testable and cross platform so we can automate deployment. Another aspect is how the software/service is designed. In software architecture there are some fundamental design philosophies like [SOLID](https://en.wikipedia.org/wiki/SOLID)-principles that is really usefull to follow when designing software. 

One problem we have today is that a lot the software we are dependend on is not following these principles, and is increasingly at odds with the way modern, cloud native computing is done.

#### The solution

We would like to focus on one or two specific _Open Source_ project of a well used statistical methods like TauArgus f.ex, where we would contribute and help to implement things like automated builds, deployments and test. And maybe even suggest best of breed software engineering principles when designing _Statistical Methods_. Here we would use all the experience we have accumulated through the work on CSPA, Serv2 & I3S and apply them to increase the technical quality of the software that have a lot of users in the Statistical community. One result of this work could also be a set of technical quality criterieas that could be used to asses Statistical software that is show cased in the list of [_Awesome official statistics software_](https://github.com/SNStatComp/awesome-official-statistics-software).