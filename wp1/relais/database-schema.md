### IS2 Workbench - Database schema

In this section we describe the database implemented for the workbench. The database has been modelled according to a process-oriented approach and the following concepts: 

- **Process design**: set of tables describing the process related to a specific business function, according to GSIM standard (business function, business process and process step, statistical method). The statistical methods available are listed in the service catalogue.
- **Process implementation**: set of tables describing ‘how’ the process will be executed. For each process step, these tables store information about the algorithm, variables (input/output) and runtime parameters. 
- **Data**: the repository of data provided by users. This repository may contain auxiliary information (e.g. edit rules, benchmark data).
- **Workflow**: set of tables managing the sequence of the process steps according to predefined process control rules.
- **Session**: set of tables managing the single working section.

The script to generate the database is available on github [is2](https://github.com/mecdcme/is2)
The ‘db’ folder contains the script is2.sql.
A brief description of the core tables of each subset is provided in the following sections.

# Process design

Based on the GSIM standard, this subset of tables refers to the design of business processes and process steps implementing a business function. The design phase also includes the choice of the statistical method, performed by a process step, to be executed at runtime.

The statistical method is defined by the combination of the following concepts:

- **Method**: description of the statistical method implemented by the algorithm.
- **Roles**: description of the method parameters (e.g. for Record Linkage, matching variables and match/unmatch thresholds). 
- **Service**: link to a business service available in the catalogue.

The following list reports the *process design* tables and a brief description of their content.

Table name  | Description
------------- | -------------
IS2_BUSINESS_FUNCTION     | Target objective or high level task
IS2_BUSINESS_PROCESS      | The set of process steps to perform one or more business functions
IS2_PROCESS_STEP          | Step associated with a single command or function call
IS2_BUSINESS_SERVICE      | Catalogue of the available services 
IS2_ROLE                  | Description of the variables related to a statistical method  
IS2_LINK_FUNCTION_PROCESS | Relation between IS2_BUSINESS_FUNCTION and IS2_BUSINESS_PROCESS 
IS2_LINK_PROCESS_STEP     | Relation between IS2_BUSINESS_PROCESS and IS2_BUSINESS_STEP 
IS2_LINK_STEP_SERVICE     | Relation between IS2_BUSINESS_STEP and the Catalogue of the available services
IS2_LINK_STEP_ROLE        | Relation between IS2_BUSINESS_STEP and the list of roles describing the statistical method parameters

# Process implementation
This subset contains the tables needed to specify input/output variables, the method signature and more in general, all the runtime parameters to execute the single instances of a process step.  

A process step corresponds to an ‘atomic operation’ executed by the ‘process execution’ engine. The procedure executed by the runtime engine is specified in the process step instance. The relation between a step and a step instance is 1:N because there can be several instructions, written in different programming languages, that can perform a given step. 

To provide the input/output of a process step instance may require to match variables and expected parameters, by assigning a specific ‘role’ to the core variables (e.g. variable=Name, role=Matching variable). The role specifies the function of a given variable and all the parameters to execute a procedure: input, output or whatever depends on the general workflow according to the single steps launched.

The following list reports the *process implementation* tables and their content.

Table name  | Description
------------- | -------------
IS2_STEP_INSTANCE         | Actual implementation of a process step. It describes the signature of a function, that belongs to a R or Java package listed in is2_app_service
IS2_PARAMETERS            | Parameters in the signature of a function 
IS2_APP_SERVICE           | Catalogue of R and Java packages
IS2_BUSINESS_SERVICE      | Catalogue of the available services 
IS2_PARAMETER_TYPE        | Parameter classification  
IS2_LINK_STEP_INSTANCE    | Relation between IS2_PROCESS_STEP and IS2_STEP_INSTANCE
