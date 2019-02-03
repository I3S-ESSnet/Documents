# Dataset catalog service

**DO**: Statistics Sweden

**RO**: Istat

**Rank**: 

**Functionalities mapped to the GSBPM**: overarching different phases

**State of achievement**:

**Distance to CSPA**:

**Technical prerequisites**: Java, MySQL

**Risks**: -

**Description**: A catalog of persisted Dimensional DataSets which includes DataStructure, SetLists  (Value Domain) and Datapoint. The catalog also include metadata about the DataSets, how the DataSet was created and in what context.

The DataSetCatalog keeps track of Dimensional Datasets. This means that each Dataset is tagged with metadata describing the context the Dataset was created in e.g. Statistical Program, Process Step, Reference Period. This metadata is searchable. Datasets are produced/created in some kind of transformation. A transformation can use zero or more datasets as input. The Datasetcatalog keeps track of what the transformation that created a Dataset looked like. As well as what other Datasets the transformation was based upon. The Datasetcatalog keeps track of each Datasets Datastructure and Datapoints. When a dataset is to be persisted, its Datapoints are always validated against its Datastructure. That is, checking datatype and codes in enumerated value domains. The Datasetcatalog keeps track of where Datapoints are stored and what reader/writer (DataPointStore) that are needed to stream them. This means that Datapoints can be stored in different physical formats and locations.

Statistics Sweden will continue the development of this service after the project has ended. If there are other parties interested in contributing to the project we will also set up a platform for continued development in a collaborative form.