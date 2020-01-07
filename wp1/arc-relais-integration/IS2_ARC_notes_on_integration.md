# IS2/ARC

## ARC integration status

### Progress

- The 19/12 version of IS2 had been forked to be able to run on Postgres

- [The documentation and the sql script](#ARC-integration-script-on-is2) materialize the first try to integrate the ARC application inside the IS2 workbench
    
    - Arc is defined as the other services already provided in the IS2 workbench - Relais, Data Editing, Data Validation
    
    - The parameters template had been defined for the ARC process steps "LOAD" and the "MAP TO MODEL"
 
### Next steps proposal

- Modify IS2 to be able to run directly on both MySQL and Postgres databases

    - The target database system (uri/driver) is already set in the application properties file
	
    - The code modification doesn't seem too expensive
	
		- Check [the storage implementation compatibility issues](#Storage-implementation-compatibility) for details

- Get a feedback on the ARC/IS2 integration script from the IS2 team

    - Are there any other implementation possible ? With RuleSet, Variabili or Runtime ?
		
    - Some ARC functionnalities had been left away because I couldn't see a way to implement them in the current version of IS2
	
        - save / copy parameters from session to session
          
		- is there any way to make Variabili or Runtime optionnal or disabled is not needed ?
		
		- the norm concept, the execution preconditions, the syntaxic error tests
		
			- it may be finally a good thing that these functionnalities aren't implemented in IS2 for the simplicity sake. To be discussed

- Review the IS2 modelization. Here is a very partial list of items :

    - What are ruleset ? Why their implementation looks so different from parameters ?
	
    - The way to store the data of files (dataset) as it looks very uncommon
	
    - A is2_business_service may have several i2_app_services (java or R class) but there is no order (see the comment in sql script)
	
    - The table is2_link_step_instance may link inconsistent data with not the same business_service id

- With IS2 team help (in Toulouse ?), start the development of one ARC execution step (LOAD step)

	- How to retrieve IS2 user parameters ?
	
	- How it works with spring batch ?
	
- Enhance the IS2 documentation to explain how to add an new application in IS2 as we did for ARC

	- I started a [step by step guide](#How-to-declare-an-application-in-IS2-step-by-step)
    
	- Explain the CLS_TYPE_IO_ID and CLS_DATA_TYPE_ID modalities
    
	- Explain the json template for parameters definition and how "dataSource" works

- Describe the INSEE and ISTAT experimentations for IS2 and ARC

    - It may be a good functionnal validation
	
    - "BPE" experimentation for INSEE

- Share the code and the IS2 application	
	
	- Pull the postgres IS2 version on a branch of https://github.com/mecdcme/is2
	
	- Deploy IS2 with ARC on the SSB cloud plateform

## Storage implementation compatibility issues

IS2 use the Hibernate framework. IS2 is already almost compatible with other database than MySQL such as Postgres.

Here is a list of improvements that we could implement to remove the last dependancies to the MySQL database system and completely respect the standard base sql.

- "order" is a reserved keyword and shouldn't be used as column name

- avoid the json types inside the database as the json types and functions are not sql standard and implemented differently depending on the database systems.

	- Use string types and make java read them as json
	
    - IS2 uses the json types to store the data from files in line. It could be better to store every file in a single data table and use the ANSI normalized view to retrieve the metadata and data.
	
- use a framework such as liquibase to initialize or patch the database

    - IS2 provides for the moment a raw sql script which is mysql database dependent. 
	
- a springbatch table had been manually modified to add 3 columns. It would maybe be better to store these data in an extra table


## ARC integration on IS2

### How to declare an application in IS2 step by step 

1. Declare the business function in is2_business_function

    1. It defines the application level. The name of the business function appears on the left menu bar and it is what the user click to enter the application.

2. Declare into is2_link_function_view_data_type the input entries of the business function which may be DataSet or RuleSet

3. Declare the business processes and link them to the business function

    1. Declare a parent business process in is2_business_process. A parent process have "NULL" in the parent field

    2. Link the parent business process to the business function
	
    3. Declare the child processes of the parent process by setting as parent field value the id of the parent business process

4. Define the process steps
    
	1. Define the business_service that is used by the process step in is2_business_service
    
	2. Add the process step in is2_process_step. A process_step calls one and only one business_service.
	
    4. Link the process step to the business processes in is2_link_process_step

5. Define the application services in is2_app_service

    1. An application service decribes how to find the R or Java code that will be executed for a particular business_service (service factory)

6. Define an instance of the application service in is2_step_instance to link it to the process step in is2_link_step_instance

> [ It may be inconsistent on the business_service
> because on one side : instance -> factory -> business_service -> process_step
> and on the other side : step_instance -> process_step -> business_service
> ]

7. Create the parameter templates in is2_parameter by the json definition :

    1. the parameter name
	
    2. the parameter title displayed in is2
	
    3. the java type if not an enum (maybe enum should be define as a type)
	
    4. if the parameter is required
	
    5. the maximum length
	
    6. the enum tables or datasource (i don't see how datasource works)
	
    7. the controls to be displayed on the screen
    
8. Define the parameters that you want to use in your business service

    1. Create a parameter in is2_app_role. Define what parameter template from is2_parameter you want to use and what CLS_DATA_TYPE_ID (???) it will be
	
    2. Link the parameters created to a business_service in is2_link_business_service_app_role


9. Create the implementation signature in is2_step_instance_signature that links the step instance and the parameters

    1. What is CLS_TYPE_IO_ID ?
	
> [It may be inconsistent on the business_service
> because on one side : parameter -> app_role -> business_service
> and on the other side : app_role -> step_instance_signature ->  step_instance -> process_step -> business_service
> ]



### SQL Script with comments

```sql=
-- Application name
INSERT INTO is2_business_function (ID, NAME, DESCR, LABEL, ACTIVE) 
	VALUES 
		(4,'ARC','File loader workbench','ARC',1);

-- required data type for the is2_business_function
-- dataset, ruleset
INSERT INTO is2_link_function_view_data_type (business_function_id, view_data_type_id) 
	VALUES (4,1);

-- Business process
-- A parent process linked to the top applciation level (business function)
-- Some child processes linked to the parent process (inner table link by the parent field)
INSERT INTO is2_business_process (ID, NAME, DESCR, LABEL, PARENT, "order") 
	VALUES 
	(9,'File loader workbench','File loader workbench','PARC',NULL,1);


INSERT INTO is2_link_function_process (BUSINESS_FUNCTION_ID, BUSINESS_PROCESS_ID)
	VALUES (4,9);

INSERT INTO is2_business_process (ID, NAME, DESCR, LABEL, PARENT, "order") 
	VALUES 	
	(91,'LOAD','LOAD ','PARC-1',9,2),
	(92,'STRUCTURIZE','STRUCTURIZE ','PARC-2',9,3),
	(93,'CONTROL','CONTROL ','PARC-3',9,4),
	(94,'FILTER','FILTER ','PARC-4',9,5),
	(95,'MAP','MAP ','PARC-5',9,6)
	;






-- implementation service declaration ?
-- and link wih process
-- process step definition

INSERT INTO is2_business_service (ID, NAME, DESCR) 
	VALUES  
		(91,'LOAD','LOAD ')
		,(92,'STRUCTURIZE','STRUCTURIZE ')
		,(93,'CONTROL','CONTROL ')
		,(94,'FILTER','FILTER ')
		,(95,'MAP','MAP ');

INSERT INTO is2_process_step (ID, NAME, DESCR, BUSINESS_SERVICE_ID) 
	VALUES 
		 
		(91,'LOAD','LOAD ',91)
		,(92,'STRUCTURIZE','STRUCTURIZE ',92)
		,(93,'CONTROL','CONTROL ',93)
		,(94,'FILTER','FILTER ',94)
		,(95,'MAP','MAP ',95);

INSERT INTO is2_link_process_step (BUSINESS_PROCESS_ID, PROCESS_STEP_ID) 
	VALUES (91,91);


INSERT INTO is2_link_process_step (BUSINESS_PROCESS_ID, PROCESS_STEP_ID) 
	VALUES (95,95);


--service factory
-- 2 factories could be attached to the same business service and no order in it
INSERT INTO is2_app_service (ID, NAME, DESCR, IMPLEMENTATION_LANGUAGE, SOURCE, BUSINESS_SERVICE_ID) 
	VALUES  
		(91,'ARC LOADER','Java package implementing ARC loader service','JAVA','it.istat.is2.catalogue.arc.service.loader',91);

-- "instance" of factory
INSERT INTO is2_step_instance (ID, METHOD, DESCR, LABEL, APP_SERVICE_ID) 
	VALUES
		(91,'arcLoader','Raw file data loader','ArcFileLoader',91);
				

INSERT INTO is2_link_step_instance (PROCESS_STEP_INSTANCE_ID, PROCESS_STEP_ID) 
VALUES (91,91);


-- Mapping phase insertion
INSERT INTO is2_app_service (ID, NAME, DESCR, IMPLEMENTATION_LANGUAGE, SOURCE, BUSINESS_SERVICE_ID) 
	VALUES  
		(95,'MAPPING','Java package implementing ARC Mapping service','JAVA','it.istat.is2.catalogue.arc.service.mapping',91);

-- "instance" of factory
INSERT INTO is2_step_instance (ID, METHOD, DESCR, LABEL, APP_SERVICE_ID) 
	VALUES
		(95,'arcMapping','ARC Mapping service','arcMapping',95);


INSERT INTO is2_link_step_instance (PROCESS_STEP_INSTANCE_ID, PROCESS_STEP_ID) 
VALUES (95,95);



-- parameters definition

INSERT INTO is2_parameter (ID, NAME, DESCR, DEFAULT_VAL, JSON_TEMPLATE) 
	VALUES 
	('910', 'LOADER_PARAMETERS', 'LOADER_PARAMETERS', NULL, 
	'{ "data":[],
	"schema":{ 
	"items":{ 
         "properties":{ 
            "FileType":{ 
               "enum":[ 
				"xml",
				"clef-valeur",
				"plat"
               ],
               "required":true,
               "title":"Type of file"
            }
            ,"Delimiter":{ 
               "maxLength":50,
               "required":true,
               "title":"Delimiter",
               "type":"string"
            }
            ,"Format":{ 
               "maxLength":1000000,
               "required":true,
               "title":"Format",
               "type":"string"
            }
	    ,"Comments":{ 
               "maxLength":1000000,
               "required":true,
               "title":"Comments",
               "type":"string"
            }
         },
         "type":"object"
      },
      "type":"array"
   }
   ,"options":{ 
      "type":"table",
      "showActionsColumn":true,
      "hideAddItemsBtn":false,
      "items":{ 
         "fields":{ 
            "FileType":{ 
               "type":"select",
               "noneLabel":"",
               "removeDefaultNone":false
            }
         }
      },
      "form":{ 
         "buttons":{ 
            "addRow":"addRow"
         }
      },
      "view":{ 
         "templates":{ 
            "container-array-toolbar":"#addItemsBtn"
         }
      }
   }
}');

-- buggy with no underscore when click on edit
INSERT INTO is2_parameter (ID, NAME, DESCR, DEFAULT_VAL, JSON_TEMPLATE) 
	VALUES
	('950', 'MAPPING_PARAMETERS', 'MAPPING_PARAMETERS', NULL, 
	'{ "data":[],
   "schema":{ 
      "items":{ 
         "properties":{ 
            "VariableName":{ 
               "maxLength":1000000,
               "required":true,
               "title":"Variable Name",
               "type":"string"
            }
            ,"VariableType":{ 
               "enum":[ 
				"bigint",
				"bigint[]",
				"boolean",
				"date",
				"date[]",
				"float",
				"float[]",
				"interval",
				"text",
				"text[]",
				"timestamp without time zone"
               ],
               "required":true,
               "title":"Variable Type"
            }
            ,"Expression":{ 
               "maxLength":1000000,
               "required":true,
               "title":"Expression",
               "type":"string"
            }
            ,"TargetTables":{ 
               "maxLength":1000000,
               "required":true,
               "title":"Target tables",
               "type":"string"
            }
         },
         "type":"object"
      },
      "type":"array"
   },
   "options":{ 
      "type":"table",
      "showActionsColumn":true,
      "hideAddItemsBtn":false,
      "items":{ 
         "fields":{ 
            "VariableType":{ 
               "type":"select",
               "noneLabel":"",
               "removeDefaultNone":false
            }
         }
      },
      "form":{ 
         "buttons":{ 
            "addRow":"addRow"
         }
      },
      "view":{ 
         "templates":{ 
            "container-array-toolbar":"#addItemsBtn"
         }
      }
   }
}');

-- -----------------------------------------------------
-- parameters list link to service implementation
-- -----------------------------------------------------



INSERT INTO is2_app_role (ID, NAME, CODE, DESCR, "order", CLS_DATA_TYPE_ID,PARAMETER_ID) 
	VALUES  
        (910,'LOADER PARAMETERS','LP','LOADER PARAMETERS',1,2,910)
		;

INSERT INTO is2_app_role (ID, NAME, CODE, DESCR, "order", CLS_DATA_TYPE_ID,PARAMETER_ID) 
	VALUES  
        (950,'MAPPING PARAMETERS','MP','MAPPING PARAMETERS',5,2,950)
		;


INSERT INTO is2_link_business_service_app_role (BUSINESS_SERVICE_ID, APP_ROLE_ID) 
	VALUES (91,910);

INSERT INTO is2_link_business_service_app_role (BUSINESS_SERVICE_ID, APP_ROLE_ID) 
	VALUES (95,950);



/* signature is the link between instance, factory and parameters */

INSERT INTO is2_step_instance_signature (ID, STEP_INSTANCE_ID, APP_ROLE_ID, CLS_TYPE_IO_ID, REQUIRED) 
	VALUES 
		(910,91,910,1,1);


INSERT INTO is2_step_instance_signature (ID, STEP_INSTANCE_ID, APP_ROLE_ID, CLS_TYPE_IO_ID, REQUIRED) 
	VALUES 
		(950,95,950,1,1);

```




.







