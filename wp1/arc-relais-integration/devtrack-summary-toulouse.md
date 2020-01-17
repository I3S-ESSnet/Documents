# IS2 ARC integration

|Track goals|Track progress|Pending concerns|
|-|-|-|
|Make is2 works on both mysql and postgres<br>Have a single code version for both database|||
||Initialization script depending on database had been developped||
||We've found a way to optimize the pivoting problem and tried to keep the json data structure but the way postgres and mySQL call function is not the same :(||
|||Figure out another data structure. Instead of storing the content of data columns in a json, store the table column name as a pointer to the target data ?|
||||
|Start ARC services from IS2 with the data and parameters declared in is2 and make output available to the user|||
||IS2 model had been reviewed to fully understand the model, input and output||
|||Update my documentation on "how to insert and application in IS2"|
|||A model constraint : steps can exchange data only if they are in the same business function. Must think about it|
||ARC had sucessfully be lauched by webservice using input data and parameters||
||Files can now be set as input parameters and not only be uploaded through dataset function : very useful for xml files or others which don't have any columns structuration ||
|||Make ARC output data available in an output dataset. It is linked with json subject but could be done now|
|||Invoke relais by webservice for R server ? IS2 should maybe be only to design application and call services but maybe not contains the service codes|

## IS2 json dataset storage
- csv structured file
file1.csv
|name|country|
|-|-|
|francesco|italie|
|romain|france|

- storage in is2 dataset or workset

|file_name|column_name|content|
|-|-|-|
file1.csv|name|["francesco","romain"]|
file1.csv|content|["italie","france"]|

