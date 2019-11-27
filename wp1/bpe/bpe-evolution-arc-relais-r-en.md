# Evolution of BPE

Evaluating a replacement for data ingestion features

The information system of the Base Permanente des Équipements[^1] - BPE
-- is mainly formed of two applications:

1.  one dedicated to data preparation through a set of SAS programs
    which are designed and launched by members of the BPE team,
2.  a webapp allowing fine-grained operations on data sources (such as
    quality setting) and exporting dissemination files. This is a Java
    application that uses SAS programs in order to implement business
    functions.

This study is mainly focused on how to replace the current SAS programs
following one of these two paths :

1.  **using existing and shared services** that are promoted in the
    context of the *Implementing Shared Statistical Services *ESSNet :
    ARC and Relais,
2.  **developping R programs** when the first option is not applicable.

The rest of this document will provide a classification following this
split.

1 Upstream sources processing
======================================

1.1 Database initialization
------------------------------------

Once a year, at the beginning of the year.

### 1.1.1   Reference data initialization

The tables used for storing the reference data are created.

Here, reference data are :

-   geographical data used by BPE (creating using the INSEE main
    geographical registry, Refigeo)
-   facilities classification scheme and the list of data sources used
    the previous year.

Data from the previous year is injected in the current year database,
Relais could be used in to perform this data linkage (thus allowing the
use of sophisticated linkage technics such as a soundex or a string
distance algorithm).

### 1.1.2    Database rotation

This specific operation will be rewritten in R.

1.2 Source data loading
--------------------------------

### 1.2.1    Specific processing

#### 1.2.1.1        Loading a file

This feature is part of the toolset of ARC, with the support of several
file formats.

Note: we must ensure that ARC is able to load Excel files (.xlsx)

#### 1.2.1.2        Variables handling

Various operations are made on input files :

-   variable creation,
-   variable deletion,
-   recoding / transcoding.

ARC provides features supporting those use cases.

#### 1.2.1.3        Rearrangement of variable content

For example, BPE needs the ability to split the content of an item into
several parts : one of the real case is to gather company name, address,
postal code from a unique input field.

ARC provides this feature set.

#### 1.2.1.4        Grouping observations

ARC provides this feature.

#### 1.2.1.5       Geographical coordinates conversion

We must be able to identify geographical coordinates (x, y) in an input
dataset, inputs which must be converted to Lambert 93 system.

Currently, this computation is made by a SAS program, available on the
internal INSEE computation platform.

Implementing this computation is ARC seems difficult, a proper analysis
should be conducted. An easier way to get out of SAS here is to use the
R version of this program, maybe already coded by the methods department
at Insee.

#### 1.2.1.6       Count and frequency

An R program will be suitable here.

#### 1.2.1.7       Formatting 

ARC provides every formatting functions needed by BPE, except for the
encoding conversion: indeed, some input files are not encoded using
UTF-8. This last use case will need an R script.

2 **Online processing**
===================================

This section deals with the SAS code that is leverage by the Java web
application. The webapp itself is not part of the analysis.

This Java application allows a BPE user to execute SAS programs in batch
mode, to visualize the result and to modify information stored in the
database.

The SAS programs are part of the following functional lots (of the BPE
process):

-   control of loaded data source (lot 3): precisely, control and load
    of rejected facilites during the importation phase (see §1),
-   online control and editing (lot 4),
-   fine-grained location of facilities (lot 5 and 7),
-   quality measurement (lot 6),
-   dissemination (lot 8).

2.1 Import tracking
-----------------------------

The user interface provides report of the import of sources data.

No SAS program is involved here.

2.2 Loaded data sources management
--------------------------------------------

In order to extract checks (ratios or thresholds), users need to extract
part of the database.

This functionality is mainly directly given by the webapp except for the
birth / maternity ratio which is computed by a SAS program.

This program could be redeveloped in R.

ARC use here is subject to condition (see architecture points further).

2.3 Quality measurement
---------------------------------

Two features are brought by this module: on one hand, it helps preparing
the quality survey (on a subset of facilities), and on the other hand it
provides the UI for the input of paper questionnaires.

It makes sense here to develop some R programs (replacing 3 SAS
programs).

2.4 Fine-grained location
-----------------------------------

The goal of this feature is to extract a subset of facilities for which
the user wants to compute the coordinates.

Those programs seems to specific to be implemented through ARC, they
will be rewritten in R.

2.5 Dissemination
---------------------------

This function builds the dissemination tables (in SAS format) from the
database.

It will be rewritten in R.

3 Architectural ponderings
======================================

3.1 Two applications
------------------------------

Two applications exist simultaneously: the application supported the
current process and a second one used during the previous year.

This solution was set up in order to cope with the need, every year, to
store two years of data at the same time (the BPE process needs to start
a yearly campaign before having finished the previous one).

3.2 Using ARC for online processing
---------------------------------------------

The online feature could theoretically implemented using ARC, but ARC
could only connect to one database at a time. Could an evolution be
planned? Or another solution ?

4 Summary
=====================

+-----------------------+--------------------+-----------------------+
| Feature               | New implementation | Remarks               |
+-----------------------+--------------------+-----------------------+
| Geo data              | ARC                |                       |
| initialization        |                    |                       |
+-----------------------+--------------------+-----------------------+
| Current and previous  | Relais             |                       |
| year linkage on       |                    |                       |
| facilities and        |                    |                       |
| sources.              |                    |                       |
+-----------------------+--------------------+-----------------------+
| Source file import    | ARC                | A format per source.  |
| (different format     |                    |                       |
| supported)            |                    | Are Excel files       |
|                       |                    | supported ? If not,   |
|                       |                    | use R.                |
+-----------------------+--------------------+-----------------------+
| Variables handling    | ARC                | It includes postal    |
| (creation,            |                    | code to city code     |
| deletation, recoding) |                    | transcoding, and the  |
|                       |                    | specific cases of     |
|                       |                    | Paris, Marseille and  |
|                       |                    | Lyon.                 |
+-----------------------+--------------------+-----------------------+
| Rearrangement         | ARC                |                       |
+-----------------------+--------------------+-----------------------+
| Observations grouping | ARC                |                       |
+-----------------------+--------------------+-----------------------+
| Conversion from GPS   | R                  | It will also be study |
| coordinates to        |                    | how to do that in     |
| Lambert ones.         |                    | ARC.                  |
+-----------------------+--------------------+-----------------------+
| Counts and            | R                  |                       |
| frequencies           |                    |                       |
+-----------------------+--------------------+-----------------------+
| File encoding         | R                  | Some problematic      |
|                       |                    | source file encoding. |
+-----------------------+--------------------+-----------------------+
|                       |                    |                       |
+-----------------------+--------------------+-----------------------+
| Loaded data sources   | R                  | The birth SAS program |
| management            |                    | to be rewritten in R. |
|                       |                    | The use of ARC here   |
|                       |                    | could be analysed.    |
+-----------------------+--------------------+-----------------------+
| Quality measurement   | R                  |                       |
+-----------------------+--------------------+-----------------------+
| Fine-grained location | R                  |                       |
+-----------------------+--------------------+-----------------------+
| Dissemination         | R                  |                       |
+-----------------------+--------------------+-----------------------+

[^1]: Permanent database of facilities, see
    https://www.insee.fr/en/metadonnees/source/serie/s1161
