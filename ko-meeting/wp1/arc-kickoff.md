# Kickstart I3S - ARC [REV DE TRAVAIL]
Last update : 2019-01-31 16:20

## Versions sauvegardées
[REV 2019-01-31 16:20 ENGLISH](https://hackmd.beta.innovation.insee.eu/96D0BABXTEak6mWJIUUNHw)
[REV 2019-01-25 17:00 FRENCH](https://hackmd.beta.innovation.insee.eu/ztI3t0UsSae_ZQ2U2fYytg)

# Attractiveness

## Contribution to statistic objectives

A statistical process includes a data acquisition phase. Multiple sources, and the more and more frequent combination of them, can provide these data (survey, administrative or private data). A converting to statistical format phase (statistics units and attributes) is necessary before statistics treatments.

The ARC (Acquisition Reception Controls) software is to receive (administrative) data given by the providers (several formats are considered, particularly XML), to control the received files compliance, and to transform administrative data to elementary statistical data. The software enables one statistician to set controls and mappings, to test them in a sandbox environment (linked to the software), and to put them into production without frequently calling on a developer.

These functionnalities/services aim the statistician’s independence and ability to adapt to the data evolutions avoiding impacts on the statistics chain.

![](global-process.png)

## Confidence in benefits

### GSBPM mapping

The Generic Statistical Business Processes Model (GSBPM 2018) presents the processes that may be followed by the National Statistics Institutes (NSIs) to produce statistical outputs.  It provides a standard framework and harmonised terminology to help statistical organisations to modernise their statistical production processes, as well as to share methods and components. The GSBPM can also be used as a template for harmonizing statistical computing infrastructures : for that reason we here conduce a simple mapping of ARC application within GSBPM phases and sub processes.

![](gspbm.png)


Main functionalities of ARC application related to data processing life cycle are linked to the GSBPM "Process" step, and more precisely to elementary treatments necessary to integrate data, engage basic cleaning and editing tasks, but also transformation operations that are necessary to convert raw data into a statistical database compliant with statistical concepts and units. This is mainly related to sub-processes going from "5.1 - Integrate data" to "5.5 - Derive new variable and units" :

  - Sub-process "5.1 - Integrate data" is related to data integration from one or more sources. According to GSBPM, the input data can be from a mixture of external or internal data sources, and a variety of collection modes, including extracts of administrative data. The result is a set of linked data. ARC is dedicated to combining data from multiple sources or combining multiples files from a same kind of data source, in order to create an integrated database.
   - Sub-process "5.2 - Classify and code" is also covered by ARC, as it includes coding routines to convert initial variable codes to a a pre-determined classification scheme.
   - Sub-process "5.3 - Review and validate" examines data to try to identify potential problems, errors and discrepancies such as outliers, item non-response and miscoding. ARC User can create testing and validating rules, which will be applied to data with detection of actual or potential errors. According to GBSPM, treatments in sub-process 5.3 are only dedicated to discrepancy and error detection, while effective data editing is done in sub-process 5.4
   - Sub-process "5.4 - Edit and impute" convers a variety of updates, often using a rule-based approach. In ARC, data editing is mainly related to filtering and basic imputation. Functionalities include  the determination of whether to add or change data, changing data values, and flagging data as changed in the process phase.
    - Sub-process "5.5 - Derive new variables and units" derives data for variables and units that are not explicitly provided in the collection, but are needed to deliver the required outputs. Through user defined rules, ARC may derives new variables by applying arithmetic formulae to one or more of the variables that are already present in the dataset, or applying different model assumptions. 
    
Previously to theses steps, ARC is also built to host raw data files that have been collected and deliver environment for storing large data collection before being processed. It thus can be used as a collection tool according to GBSPM sub-process "4.4 - Finalise collection",  oading the collected data and metadata into a suitable electronic environment for further processing.

Because it includes sandbox creation and testing procedures of user rules, ARC application is also  compliant with GSBPM subprocesses dedicated to "2.5 - design processing" and "3.6 - test statistical business process".

- "2.5 - design processing" can include specification of routines for coding, editing, imputing, estimating, integrating, validating and finalizing data sets.
- "3.6 - test statistical business process", which includes activities to manage a pilot the statistical business process, including testing processing rules on data.

If selected within the ESSNet I3S process for shared services, further developments of ARC would also be engaged with new functionalities,that would expand the GSBPM coverage of ARC to the GSPBM 5.7 (Calculate aggregates) and GSPBM 6.2 (Validate output) sub-processes, with the ability to use aggregations to perform advanced controls, filtering, or formatting, and also produce indicators and countings (see below, "iteration 3 : add an aggregate module").


### Features and functional description

#### Overview
The ARC software features functions of configuration and execution for file processing pipelines.

The processing of a file in ARC is materialized by a sequential execution of elementary services which are also called "processing module". Theses modules are instantiable in disjoint execution environments called "sandbox".

The choice, the scheduling, or the internal operations of the modules are based on user written rules defined for the chosen sandbox. ARC therefore allows the user to experiment with different processing rules for identical files in different sandboxes.

ARC provides a web interface to lead the user through the rules definitions. The language for defining complex rules is based on the SQL database language.

The ARC modules treatments are performed by the database and parallelized by file at runtime.
The database keeps track of the actions of the application and allows the synchronization service to automatically rebuild a consistent system if necessary. User defined rules and metadata are stored and versioned in the database.

ARC currently supports two types of metadata. 
The models identify the normalized relational models defined by the user. They are used to define the rules and store the output generated by the statistical formatting module.
The external tables integrated by the user are used by the rules of the different modules.

#### List of the ARC treatment modules


| Module Name      | Mode | Order | Description |GSBPM|
| ---------------- | ---------| ------------------------- | ----------- |----------- |
| Synchronize| optional noparallel | 1 | Rebuild the database and file system in a consistent state with the database. <br> Execute file replays or delete commands. <br> Copy the rules of the configuration space into the sandbox of execution so that they are taken into account in the execution of the subsequent modules |
|Register| mandatory parallel| 3| Register a set of input files and update the file system | 4.4 |
| Identify | mandatory parallel | 4 | Apply the rules of the module to determine the "category" of the files. <br> The rules written by the users have a global input key called "category". <br> This key identifies the different chains of treatments. The category and the sandbox determines which rule sets to apply to the file when processing the subsequent modules | 5.2 |
|Load|mandatory parallel | 5 | Apply the rules of the module to instantiate the proper file reader to load the data without transformation in the database. <br> Store the file hierarchy of structured files as XML for the subsequent modules| 5.1 |
|Structure | optional parallel|>5|Flatten the previously loaded structured data consistently. Apply the rules of the module for advanced structuration features | 5.1 |
|Control|optional parallel|>5|Apply the correction and control rules| 5.3
|Filter|optional parallel|>5|Apply a filter rule to exclude records| 5.4
|Format |optional parallel|Last mod|Transform and store loaded data in a standard user-defined data model| 5.5


#### Advanced features of file and data manipulations
ARC doesn't require a XSD validation  or rejection to load XML files into the database. The controls are decoupled from the loading of the data and may be implemented in the subsequent and optional control module.

The load module has the ability to convert a flat unstructured file into an XML file. The user defines the expected XML structure by the rules of the module.

The structure module flattens the loaded structured data in a consistent way. It provided advanced features such as joins between data fields, eliminations of duplications or block based copy operations. 


#### The statistical formatting module as an interface for the information system
The data generated by the format module are stored into one of the data models chosen and built by the user.
The registered client softwares can query data and models structures through the data retrieval Web Service provided by ARC.
In practice, the formatting module acts as an interface between the input files and the expected model used by the client softwares.
The evolutions of input files can thus be more easily decoupled from the statistical processing carried out by the client softwares.

####  Write the ARC user defined rules
The user sets ARC modules by writing rules.
* simple rules to parametrize the module's operation
* complex rules interpreting the data processed by the module

The complex rules of data manipulation or condition checking rely on the SQL database language. They are checked syntactically on input.
The structuring rules are written in XML language.

#### From sandbox to production
Test and validate the user defined rules may be carried out by the user by executing the modules on the application sandboxes.

The web interface provides for the user and for each sandbox the ability to apply his new set of rules, iterate over the modules, monitor the reports or download the data.

The implementation of modules is identical bewteen the production and the sandbox as the production environment is just defined as a particular sandbox.

The user can deploy his rules in the production environnement by the web interface. The deployed rules don't become effective until the invocation of the synchronize module.

#### Performances
ARC processes files in parallel. The application was originally designed to handle massive flows of moderately large files has been optimized to be as effective in the processing of very large files (~ 50GB).

#### Software architecture and deployment
ARC consists of a web java application (java 8, tomcat 8), a java processing server (java 8), and a postgres database 9.6.
The java module "synchronize" handle the rebuilds and the upgrades of the database according to the version of the java code.
ARC has already been containerized with Docker. This way to deploy ARC will be supplied as part of the I3S project.

## Stakeholder commitment

Three instances of the ARC application are running in production within the INSEE information system of employment and income called "SIERA". The main instance loads monthly the 2.5 millions of income files declared by the French companies through a XML format called "DSN". The others instance are used monthly to load large data files into the information system. ARC is currently under study to be deployed for the SIERA future projects and for the other INSEE information systems.

The internal INSEE community around ARC is fairly active and its functional base is evolving at the rate of a [major version per year since 2016] (# Status-of-software). The ARC application is maintained in production by a maintenance team of 2 developers. The SIERA project team and a dedicated expert technically help the other projects to reuse ARC

In total, 6 developers from the national computer development department of Orléans are currently working on developments and supports around ARC.

INSEE would mobilize 1.5 developers to integrate ARC in the ESSNET I3S project for the period 2019-2020.

# Achievability


## Confidence in delivery

### Status of software

The ARC application is used in effective statistical processes from nearly 3 years from now on (several instances of ARC have been deployed from June 2016 within INSEE statistical processes). It has been strengthened year after year, in a continuous quality management. 

| Version name | Purpose of the version | Start date|Release date| Features implemented |
| ------- | ---| ----- | ----|---- |--|
| v1-DSN | Monthly formatting of 2.5 million XML employee file | Jan 2015 | June 2016 | 1. Full pipeline for XML files <br> 2. Optimized performance on massive flows of small files <sup> 1 </sup> |
| v2-CTS | Multisource Hub for Large Files (50 Million Lines, 500 Columns) | Mar 2017 | Nov 2017 | 1. Delimited flat and key-value type files loader<br> 2. Structuration feature for flat and key-value type files <br> 3. Parallel modules execution by file
| v3-CTS | Performance on all file types | Jan 2017 | aug 2018 | 1. Isolation of file pipeline <br> 2. Optimized performance on large files <sup> 2 </sup> |
| v4 | Quality Iteration | Sep 2018 | Jan 2019 | 1. Refactor of the java classes and models <br> 2. The processing chain is no longer static but configurable by the user |

<small> 1. The integration of 2.5 Million complex XML files lesser than 200 MB takes 5 days of processing </small>
<small> 2. The parallel integration of 2 files of 50 GB of data (uncompressed) or 50 million line and 150 columns takes 10h without flat file to XML restructuration. The integration of a single file takes 8h. </small>

### Alignment with CSPA

The service was initially developed without specific considerations for its CSPA compliance or its reusability by other NSIs. However, it was natively built as a potentially shared service with other statistical processes within French NSI : ARC was designed as an elementary building block dedicated to data integration and elementary data editing (review and control though user specified rules).

As a consequence, its design is quite independant on local technical environment (and can be nested in a docker file for international deployment), but some work has still to be done in order to reach common standards such as CSPA. The following points had to be improved through the I3S ESSNet :
· Basic code review in order to write it fully in English 
. Advanced code refactoring so as to re-build the application as services.
· Documentation (functional and technical)
· Release as open source ESSnet submission

## Capacity of competence (community, FOSS)

The maintenance and project team of ARC work at the software development center of Orléans (SNDIO) and are specialized in data manipulation process.

| Development item | Complexity | Competence<br>currently<br> available <br>(number of developers)|
|---- | --| -|
| Standard global java web architecture<br> - java 8, tomcat 8, postgres | low | 6 |
| Simple and old technologies for the web interfaces<br>Self developped generic component to generate view<br>- javascript, ajax, strut 2| moderate | 6 |
| Basic java framework and functionalities<br>- spring, java 8 but no lambda expression | low | 6 |
| The code complexity may be hard because of the genericity <br>- especially in the structure and in the statistical format modules |   high | 3 |
| Database processes are optimised and complex| high | 2 |


Both of the project and the maintenance are managed by iterative methods.


## Adequacy of ressources provision (shared, replicate, interoperable)

### Risk analysis
| Risk | Probability | Criticity | Obviation |
|----|-|-|-|
|The main developper will quit his function in the middle of the project |sure|severe|Train another developer as soon as possible.<br>Focus first on the quality of the code and documentation to make the application easier to undertake.<br>Already engaged |
|Development ressources shortage due to external simultaneous operations|likely|moderate|Break down the projet into small and consistent realeases to meet priorities.|
| Inadequation between the application used in production and the project|possible|moderate|Automate the release upgrades.<br>The maintenance team and the application owner must validate the new functionalities and test at least one release out of two.|

# Affordability
## Implementation / operational costs

### Four development focus for the project
1. Quality - Upgrade the code to conform with the open source collaboration level
2. Sharing - Use the development standards including the ones provided by the ESSNET to promote the reusability
3. Evolution of functionalities - Extend or modify the base features to fulfill the emerging needs
4. Services and modularity - Review the design of services

### Project planning proposal
The project is proposed to be broken down in 4 iterations, each providing a new stable release of the application ARC.

The iterations are built to cover a unique developement focus among those previously mentionned. This option may improve the clarity of the releases, reduce the costs of similar developments and improve the certainty about a final delivery.

### Iteration 1 : Develop an opensource release
Development focus : Quality
Duration : 6 months
Start date : feb 2019
End date : jul 2019

| Scope | Task | From | To
|--------|------|--|--|
| All modules | Use english as a language of work for the code, the database, the web interfaces and the documentation | in progress | Jun 2019
| All modules | Repackage of INSEE internal libraries | now | feb 2019
| All modules | Cover the code by tests (Coveralls / Travis CI) | feb 2019 | Jun 2019

### Iteration 2 : Use VTL as a language of rule definition
Development focus : Sharing
Duration : 6 months
Start date : jul 2019
End date : dec 2019

| Scope | Task | From | To
|--------|------|--|--|
| Load, Structure | Serialize the storage of the hierachy of json or xml structured files| Jul 2019 | Sep 2019 |
Load | Add standard implentations to loader <br> (JSON, Read XML Attributes) | Jul 2019 | Sep 2019 |
| All modules | Interface the user defined rules with VTL | Sep 2019 | Dec 2019 |
| Register<br>Meta Data | Add features for remote file repositories | Sep 2019 | Nov 2019 |
| All modules | Delivery by Docker container | Nov 2019 | Dec 2019

### Iteration 3 : Add an aggregate module
The addition of an optional aggregation module simultaneously addresses two distinct business needs
1. Produce indicators and countings
2. Use aggregations to perform advanced controls, filtering, or formatting

The aggregate module would expand the GSBPM coverage of ARC to the GSPBM 5.7 and GSPBM 6.2 processes.

Development focus : Evolution of functionalities
Duration : 2 months
Start date : jan 2020
End date : feb 2020

| Scope | Task | From | To
|--------|------|--|--|
|<new module> Aggregate| Implement user defined aggregates | jan 2020 | feb 2020 |

### Iteration 4 : Generalize the context variables used by the modules
Item : Services and modularity
Duration : 8 months
Start date : apr 2020
End date : nov 2020

| Scope | Task | From | To
|--------|------|--|--|
| All modules | Review of the existing services<br>Check the entry level of the concepts | apr 2020 | Nov 2020
| Identify | Generalize the context variables used by the modules| apr 2020 | Nov 2020 |





## Alternatives certainty


## Legal compliance
Licencing for OpenSource