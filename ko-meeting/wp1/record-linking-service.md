# Record linking

**DO**: Istat

**RO**: Insee, INE

**Rank**: 2

**Functionalities mapped to the GSBPM**: 5.1 Integrate data

**State of achievement**: Relais Version 3.0

**Distance to CSPA**: *not fully compliant* with CSPA principles. Licensed under EUPL 1.1.

**Technical prerequisites**: R, Java, MySQL

**Risks**: -

**Description**: Record Linkage (RL) deals with the problem of identifying pairs of records coming from  different sources and representing the same real world entity. Integration of different data sources and improvement of the quality of single sources are only some of the real application scenarios that need to solve the RL problem. In Official Statistics, to cite just a single example, the need of performing a RL task arises whenever one tries to integrate statistical survey data with data coming from administrative archives, due to lacking or unreliable common record identifiers. RL can be applied in several applications, including: enriching the information stored in different data-sets; de-duplicating data-sets; improving the data quality of a source; measuring a population amount by capture-recapture method; checking the confidentiality of public-use micro data. Indeed, record linkage can be seen as a complex process consisting of several phases involving different knowledge areas; moreover, several different techniques can be adopted for each phase. Several methods have been proposed to face RL problems and many independent software implementations of traditional methods exist. The aim of the service is to focus on some specific commonly used deterministic and probabilistic record linkage functions and provide a service-based implementation for them. Istat will leverage its recognized expertise in the RL field in order to develop this service. Insee and INE are interested in reusing this service in their production processes. The released version of the software is available at: https://www.istat.it/en/methods-and-tools/methods-and-it-tools/process/processing-tools/relais.