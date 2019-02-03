# Error correction

**DO**: Istat

**RO**: 

**Rank**: 4

**Functionalities mapped to the GSBPM**: 5.4 Edit & impute

**State of achievement**: Released version 1.0

**Distance to CSPA**: available in CSPA catalogue

**Technical prerequisites**: R, Java

**Risks**: -

**Description**: This service allows to check data consistency according to a defined set of editing rules. These rules can be expressed in terms of constraints and applied at unit or variable level. The service will be mainly based on the wrapping of R package ‘Validation’ and the functionalities to be implemented can be split:

  * checking editing rules consistency; 
  * applying editing rules to a dataset, in order to detect wrong values;
  * deterministic imputation, based on if-then rules.

The user will be also able to modify, add or cancel a single rule and will visualize some reports to assess the result of the procedures invoked. 
The proposed service is an enhanced version of the “Error correction”, currently available on the CSPA catalogue.