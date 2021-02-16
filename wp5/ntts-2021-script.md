# NTTS 2021 presentation script

## "Powerpoint" intro

Duration: 30 seconds max

Words: 50

*IT Manager*

As you can see on slide 84, our IT costs are surging. We have too many monolithic legacy systems, and we are facing vendor lockdown and lack of expertise. Standardizing our production process and sharing developments with other statistical organizations could help us, but we don't know where to start?

*Mauro*

Haven't you heard of I3S?


## I3S intro

Duration: 30 seconds max

Words: 100

Sharing services is always mentioned as a way of reducings costs and improve industrialization of the statistical production but has inpractice often been hampered by differences in architecture and techologies.

I3S stands for "Implementing Shared Statistical Services". It's an ESSnet focused on making sharing and reusing services practicel between statistical organizations, based on standards and models developed by our commmunity.

France, Italy, Norway, Portugal and Sweden have worked together to produce concrete advice, guidelines and examples that can help others to reuse existing services and to create reusable services. Aspects such as architecture, service deployment and communication have been covered.

## Architecture

Duration: 2,5 minutes

Words: 200

To make sure that services are created in a way that makes them easy to integrate in other statistical organisations, we have the CSPA-standard that provides support for architects. But sharing and reusing services is often not the only goal for you architecture. It it quite common to also have other goals for your architecture such as moving from legacy to cloud or SOA technology, achieving better enterprise data management or enabling more agile business processes. Within the I3S project we build upon the CSPA standard and see how we can combine the goal of sharability with other commonly occuring goals for your architecture.

The architecture guidance from the I3S project describe aspects and concepts around architecture and how these can be used and combined to create an architecture that allows for different goals to be achieved. The guidance also dives deeper by providing a cookbook on code-level that shows practical schoolbook-examples as well as examples from real situations where the guidance is being used. This makes the guidance more practical and useful for other roles such as developers.

--> Jakob

## Developing services

Duration: 2,5 minutes

Words: 250

ARC / Relais

One of the main goals of the I3S project is to develop, either from scratch or from existing components, new statistical services. In I3S we worked three services: PxWeb, ARC and RELAIS. 

The Px suite is a collection of programs developed for the distribution and processing of statistical tables. They offer diverse possibilities to distribute and edit even large statistical tables, and to change structures, combine tables, make calculations and convert into other file formats. PxWeb is a free web-based table distribution system for statistics producers. All Nordic Statistical Institutes use the PxWeb system.

The ARC software (from the French: Acquisition - Réception - Contrôles), developed by INSEE, allows to receive data supplied by data providers, to control the compliance of the received files versus a predefined data model, and to transform input data into elementary statistical entities. ARC software enables the statistician to define and apply controls to the input data, to test them in a sandbox environment, and to put them into production without the support of IT experts.

Relais (Record Linkag At IStat), developed by Istat, provides an integrated environment to solve a wide range of record linkage problems. The software has been implemented assuming that a record linkage process may result from the combination of different sub-phases to achieve the best data integration solution. The core logic in Relais includes a set of algorithms implemented in R and Java allowing the execution of two different record linkage approaches (probabilistic and deterministic linkage).

Both ARC and Relais have been re-designed according to CSPA principles and released as open-source software.

Another important goal of the project is related to service reuse.  Insee was looking at enhancing the production process of its Permanent Database of Facilities, by reusing RELAIS, and in return Istat proposed to define a reuse scenario for Insee's data acquisition software ARC. 

The close cooperation between ARC and Relais teams has resulted in a much higher level of quality and functionality of both services. They are now integrated in a common framework that could prefigure a future "statistician workbench" with shared user interface, process parameter definition, data access methods.

## Deploying services

Duration: 2 minutes

Words: 200

The ESSnet has also specified innovative and standardized methods for the deployment of statistical services on cloud platforms (public or in-house). These include technologies like containerization or infrastructure as code, and covers functionalities like providing more security, scalability and platform-independance.

Deploying services using these methods hugely improves the possibilities to share them, but it is also beneficial for internal use within statistical organizations because it fosters industrialization, traceability and exploitability of services.

All the software tools recommended by the ESSnet are open source, and they can in many cases replace expensive proprietary solutions.

Add something about how we did it (through deployathons) which allows improve shared skills

## Conclusion

Duration: 1 minute

Words: 100

*Back to the conversation between Mauro and the IT manager*

  * Open source communities (add something about prolonging collaboration based on Istat-Insee collaboration)
  * How to learn more?

(note: put the I3S logo(s) somewhere)
