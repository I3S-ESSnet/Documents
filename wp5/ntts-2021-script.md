# NTTS 2021 presentation script

## "Powerpoint" intro

Duration: 30 seconds max

Words: 50

Points from the Miro post-it:

  * Increasing cost of dev/gov
  * Legacy
  * Difficult to find expertise
  * Lack of re-use

Mauro steps in: "Haven't you heard of I3S?"


## I3S intro

Duration: 30 seconds max

Words: 50

I3S is an ESSnet focused on how to share statistical services in practice


## Architecture

Duration: 2,5 minutes

Words: 250

Guidelines, principles

--> Jakob

## Developing services

Duration: 2,5 minutes

Words: 250

ARC / Relais

One of the main goals of the I3S project is to develop, either from scratch or from existing components, new statistical services. In I3S we worked on ARC and RELAIS. 
The ARC software (from the French: Acquisition - Réception - Contrôles), developed by INSEE, allows to receive data supplied by data providers, to control the compliance of the received files versus a predefined data model, and to transform input data into elementary statistical entities. ARC software enables the statistician to define and apply controls to the input data, to test them in a sandbox environment, and to put them into production without the support of IT experts.
Relais (Record Linkag At IStat), developed by Istat, provides an integrated environment to solve a wide range of record linkage problems. The software has been implemented assuming that a record linkage process may result from the combination of different sub-phases to achieve the best data integration solution. The core logic in Relais includes a set of algorithms implemented in R and Java that allow to execute two different record linkage approaches.
Both ARC and Relais have been re-designed according to CSPA principles and released as open-source software.
Another important goal of the project is related to service reuse.  Insee was looking at enhancing the production process of its Permanent Database of Facilities, by reusing RELAIS, and in return Istat proposed to define a reuse scenario for Insee's data acquisition software ARC. This started an intense phase of cooperation on both software, resulting in important evolutions both on ARC and Relais to integrate them and enrich the capabilities provided by both.

## Deploying services

Duration: 2 minutes

Words: 200

The ESSnet has also specified innovative and standardized methods for the deployment of statistical services on cloud platforms. These include technologies like containerization or infrastructure as code, and covers functionalities like securization, scalability and platform-independance.

Deploying services using these methods hugely improves the possibilities to share them, but it is also beneficial for internal use within statistical organization because it fosters industrialization, traceability and exploitability of services.

All the software tools recommended by the ESSnet are open source, and they can in many cases replace expensive proprietary solutions.

## Conclusion

Duration: 1 minute

Words: 100

Back to the conversation between Mauro and the IT manager

  * Open source communities
  * How to learn more?

(note: put the I3S logo(s) somewhere)
