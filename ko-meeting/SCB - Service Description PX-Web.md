# Service Description of PX-Web
PX-Web used for publishing statistics in a database at the web and is since 1 January 2016 free of charge for Swedish government agencies and municipalities, international NSI:s and international organizations of statistics in about 80 countries. PX-Web is developed by Sweden, Norway and Denmark.

There is currently a process to make PX-Web Open Source and an ongoing development to extend the functionality of the service.

## Detailed functionalities mapped to the GSBPM 
PX-Web supports process 7 dissemination in GSBPM. PX-Web handles dissemination of data tables and diagrams on the web.

## State of achievement / functional coverage 
PX-Web can be used stand-alone och with other systems. PX-Web can handle multiple data sources for storage like PC-Axis files och database. All application settings can be modified with administration tools. 

## Distance to CSPA: internationalized? open source? service-oriented?
PX-Web fulfils the following CSPA features: 
- F1. Documentation
- F2. Internationalization
- F6. Security solutions
- F8. Sandboxing for exploration([Demo](https://www.h6.scb.se/pxwebtest)) 

In the near future we hope to fulfill the following CSPA features:
- F3. Open Source
- F9. Containerization

## Technical prerequisites
Today PX-Web runs under IIS on a Windows machine. PX-Web I distributed in a zip-archive that is unziped directly on the server. Through the administration tool included configurations can be made to PX-Web. In the future we want to be able to make PX-Web available in containers and make the Core based on .NETCore.

## Risks
The main risk for this project is the lack of human resources in the organization.
