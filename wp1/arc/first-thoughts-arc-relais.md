# Toughts about the integration between ARC and Relay

> [draft version with personnal toughts (manuel)]

- [Integration and module](#integration-and-module)
  - [RELAIS](#relais)
  - [ARC](#arc)
  - [Does a RELAIS phase could be an ARC processing module ?](#does-a-relais-phase-could-be-an-arc-processing-module-)
- [File processing](#file-processing)
  - [RELAIS](#relais-1)
  - [ARC](#arc-1)
  - [RELAIS inputs two files. How to process with two files in ARC ?](#relais-inputs-two-files-how-to-process-with-two-files-in-arc-)
- [User Interface](#user-interface)
- [Statistical calculations](#statistical-calculations)
  - [RELAIS](#relais-2)
  - [ARC](#arc-2)
- [User interface](#user-interface)
  - [RELAIS](#relais-3)
  - [ARC](#arc-3)
  - [Add indicators and vizualisation module in the rule definition screen ?](#add-indicators-and-vizualisation-module-in-the-rule-definition-screen-)

## Integration and module

### RELAIS

- the relais process looks like split in several phases
A relais phase seems to be made up by
    - a user configuration
    - a processing phase generating some outputs

### ARC

- the processing of a file in ARC is split in "processing modules". 
    > the processing of a file in ARC is split in "processing modules". The core idea was to standardize the container of the new functionnalities that could be added to the pipeline process, as some kind of brick building. More recently, it emerges these bricks should be made optionnal, invertible, or used several times in the processing of a file.
    > A web user interface per module for configuration

### Does a RELAIS phase could be an ARC processing module ?

- an ARC module looks a lot like a RELAIS phase
- Data cleaning : it looks like a big yes. It looks like it could be even be used out of RELAIS context .. It looks like ARC mapping on some aspects but with lot more functionnalities and standardization
- choice of matching variables
    - calculate default indicators to guide user in configuration ?
- ... to be continued

## File processing

### RELAIS

Both of the two tables must be processed on data cleaning phase

### ARC

- ARC presently processes file by file independently
    - a recent test shows that it is possible to link 2 files in the mapping phase but it is really not optimised neither well modelized and the parallelism will have to be taken in consideration
- ARC can use external static tables such as modalities table or repository

### RELAIS inputs two files. How to process with two files in ARC ?

- Does the use of two tables in RELAIS process prevent from using external static tables ?
    - maybe it could be if the repository is already "cleaned" ?
- A need to use relais on 2 loaded files ?
    - Would be nice for matching purposes but must rethink the ARC file pipeline. Need a way to tell the application that these two files must be batched together. There is an archive concept into ARC (archive is like a zip file that contains several files). Could we add a functionallity to build the ARC processing pipeline not only for individual files but for archives too ?


## User Interface

## Statistical calculations

### RELAIS
Looks like lot of complex statistical calculations in RELAIS. 

On user guide page 4, it is written :
> It has been implemented using a relational database architecture, in particular it is based on a mySql environment that is also in line with the open source philosophy of the RELAIS project.

Was the process implemented on mysql or was Mysql used to store the data and the process was processed in R or java ?

### ARC

All current ARC modules process are SQL based and are executed by the Postgres database. Tough, ARC use Java and a java implementation would certainly work very well too.

(Do you know if RELAIS java process is disk based or ram based ? if ram based, may have some difficulties to process large files)
Asking that because GEOLOC use almost the same algorithm (but in a lot less sophisticated and configurable version) to geolocalize large data files (~30 millions of french adress). RELAIS could be used on a project like GAIA too for the same purpose. One day, we could have to process european files size too.

Postgres cannot natively do complex statistical calculations.
It could be an opportunity to build native statistical function in a SGDB (postgres is now very friendly with Python). But this is a costly way and maybe a whole new project.


## User interface

Oh… Graphics ! I would love to see some in ARC ! The RELAIS user interface looks like a java swing client. It could be a good start for the integration between the two applications to develop a RELAIS web user rule interface for one of the relais phase inside the ARC module configuration web user interfaces.

### RELAIS

RELAIS configuration cycle seems to be very iterative : watch indicators and data produced, configure, try.

### ARC

The ARC user configuration is iterative too but maybe not as much as required in RELAIS.

### Add indicators and vizualisation module in the rule definition screen ?

First, there is no indicator class in ARC and all is data for now. There is also currently no data visualization in ARC.
ARC user can presently get the content of a module outputs in the monitoring screen of the web interface but it is just a data export to file feature.
There is also no direct interface implemented for the user to navigate from the rule definition screen to the module output export functionnality of the selected sandbox.