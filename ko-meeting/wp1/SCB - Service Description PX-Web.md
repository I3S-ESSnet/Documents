# Service Description of PX-Web

**DO**: Statistics Sweden

**RO**: Istat

PX-Web used for publishing statistics in a database at the web and is since 1 January 2016 free of charge for Swedish government agencies and municipalities, international NSI:s and international organizations of statistics. [Examples](https://www.scb.se/sv_/PC-Axis/Programs/PX-Web/PX-Web-examples/)

A shared service for dissemination of statistics would be created by transforming the currently used closed source solution to an open source solution. The transformation would include adapting to open standards such as .NET Core and HTML5 as well as assuring that the service can be used in cloud and/or containerized environments.
There is currently a process to make PX-Web Open Source and an ongoing development to extend the functionality of the service.

Statistics Sweden will continue the development of this service after the project has ended. If there are other parties interested in contributing to the project we will also set up a platform for continued development in a collaborative form.

## Detailed functionalities mapped to the GSBPM

PX-Web supports process 7.2. Produce dissemination products in GSBPM. PX-Web.

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

The main risk is the lack of human resources that can work with the project.
