# Service Description of Dataset catalog

**DO**: Statistics Sweden

**RO**: Istat

Statistics Sweden are currently in the design phase of creating a service called the Data Set Catalogue. The ambition with the service is to serve as a GSIM based, cross process and cross survey data catalogue. For each data set registered within the catalogue the following is stored:
- pointers to the physical location of the data points
- links to metadata for each used data structure
- context/survey that created the data set

Variations in physical storage of the data points are resolved by the concept och write- and read adapters. This offers full flexibility in choice of persistence technology as well as enabling migration in to the catalogue for legacy system storage.

Objectives:
- More efficient data sharing between process steps within and across statistical program boundaries.
- Centralized authorization.
- Enforced version control.
- Simplified fulfillment of GDPR and other data protection regulations.
- Consistency between consumers though the concept of steady states.

Statistics Sweden will continue the development of this service after the project has ended. If there are other parties interested in contributing to the project we will also set up a platform for continued development in a collaborative form

## Detailed functionalities mapped to the GSBPM
The data set catalog is a building block that is process agnostic.

## State of achievement / functional coverage
See service description above.

## Distance to CSPA: internationalized? open source? service-oriented?
The principles of CSPA will deeply influence the outcome of the service. GSIM Data Set and GSIM Data Structure are basic concepts within the solution.

## Technical prerequisites
Since CSPA alignment is important this will not be a significant problem area. 

## Risks
The project is still in an early phase and faces a number uncertainties.
