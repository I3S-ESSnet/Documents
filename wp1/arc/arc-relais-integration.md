# ARC-RELAIS integration

This page presents the results of a two-day workshop between Istat and Insee in Paris (30 September - 1 October 2019).

The main goal of the workshop was to compare ARC and Relais at the functional and technical levels, and to derive different integration scenarios.

## Comparison between ARC and RELAIS

The respective GitHub repositories are:

  * For ARC: https://github.com/InseeFr/ARC/
  * For RELAIS: https://github.com/mecdcme/is2

### Terminology

RELAIS uses the GSIM terminology, for example: Business Function, Business Process, Business Step (should be Process Step).
ARC terminology is more specific: 'Norm family' means 'Target data model', 'Norm' means 'File transformation process', etc.

### Functional integration

### Technical integration

Both applications are Java-based. Tomcat 8.5 is used in both cases. The database is different: MySQL for ARC and PostgreSQL for RELAIS. Tests made during the workshop show that porting RELAIS to PostgreSQL seems feasible.

#### Existing architecture

##### ARC

![ARC architecture](https://raw.githubusercontent.com/I3S-ESSnet/Documents/master/wp1/arc/img/arc-architecture.png)

##### Relais

![Relais architecture](https://raw.githubusercontent.com/I3S-ESSnet/Documents/master/wp1/arc/img/relais-architecture.png)

##### Relais

## Integration scenarios