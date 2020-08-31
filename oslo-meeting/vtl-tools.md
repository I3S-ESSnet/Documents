# I3S ESSnet "Oslo" meeting - Presentation on VTL Tools

## Reminder about VTL


## Recent developments on VTL

### Update of grammar 2.0 published

Also upgrade to SDMX 2.1.

Lots of improvements, but remaining inefficiencies (duplication of scalar/component expressions).

Governance is still unclear. Grammar evolution was untraceable. Feedback not organized.

## Panorama on tools

### Eurostat

[Interpreter and sandbox](https://github.com/eurostat/VTL)

Editor and rule manager

### Statistics Norway

[java-vtl](https://github.com/statisticsnorway/java-vtl)

### Banks

#### ECB

[BIRD tools](https://www.ecb.europa.eu/stats/ecb_statistics/co-operation_and_standards/reporting/html/bird_dedicated.en.html). VTL is used for validation and transformations: details on the [methodology](https://www.ecb.europa.eu/stats/ecb_statistics/co-operation_and_standards/reporting/html/bird_methodology.en.html) page. Some unlicensed code on https://github.com/DGSbird, but current work seems to happen in the [Eclipse Free Bird](https://projects.eclipse.org/projects/technology.efbt) project (see also https://www.eclipse.org/efbt/index.html).

#### Banca d'Italia

[VTL E&E](https://vpinna80.github.io/VTL/), mostly Java, R packaging and Jupyter notebook, EUPL 1.2 

### Other NSIs

Poland, Italy: VTL -> SQL translators

## French developments

### Common features

Generation from grammar via ANTLR

Open source

### JavaScript Tools

[VTL Tools](https://github.com/InseeFr/VTL-Tools)

### Java Tools

[Trevas](https://github.com/InseeFr/Trevas)

#### Use  case

#### Demo

### R Tools

[darkr](https://github.com/romaintailhurat/darkr)