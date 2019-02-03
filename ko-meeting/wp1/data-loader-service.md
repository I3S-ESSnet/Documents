# Generalized data loader

**DO**: Istat

**RO**:

**Rank**: 

**Functionalities mapped to the GSBPM**: 4.3. Run collection

**State of achievement**:

**Distance to CSPA**:

**Technical prerequisites**: Java, MySQL

**Risks**: -

**Description**: This service is implemented to load excel, or csv files in a structured database. The values in each cell are extracted and associated to one or more preloaded classifications defining data dimensions. By this web application based on an internal tool, excel files (having one or more sheets) are uploaded in standardized multidimensional data structures (as shown in the following figure).

![Data loader](data-loader.png)

The specific functionalities to implement are:
  - Data uploading;
  - Classification uploading;
  - Definition of rules for mapping different classifications;
  - Uploaded data consistency check.
