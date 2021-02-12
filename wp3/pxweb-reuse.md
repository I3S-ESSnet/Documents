# Implementing Shared Statistical Services - Reuse Report

## 1. Introduction

### Reporting organization
Statistics Norway (SSB)
### Unit
702 IT-Architecture
### Report version
v0.0.2
### Report date

### Contact mail

## 2. Service reused

### Publisher
Statistics Sweden (SCB)
### Name
PxWeb
### Version
PxWeb 2020

### Main functionalities
PxWeb is used for publishing statistics in a database on the web. The PxWeb application consists of two parts:

* **Administration interface** - The Administration interface is used by PX-Web administrators to manage and maintain their PX-Web installation.
* **User interface** - The User interface is the part of the application that is exposed to the end users, the actual dissemination application.

The statistical data that should be disseminated could either be stored in PX file located locally on
the Web server or remote in a SQL server in a database having the Common Nordic Meta Model.
PX-Web is also able to combine the two types of data sources.

### Links (code, documentation...)
* Souce code
   * https://github.com/statisticssweden/PxWeb
* Documentation
  * https://www.scb.se/en/services/statistical-programs-for-px-files/px-web/
*  Presentations at last PX meetings
   * 2020: https://www.scb.se/px-meeting-2020
   * 2019: https://www.scb.se/PxMeeting2019
   * 2018: https://www.scb.se/en/services/statistical-programs-for-px-files/px-web/international-px-meeting/

## 3. Service reuse

### Context
PxWeb comes from the PC-Axis

> "For the 1990 Swedish Population Census PC-Axis was developed"
> [PC-Axis Family Software - A Consortium for Dissemination of Statistics (2004)](https://www.nass.usda.gov/mexsai/Papers/pcaxisp.pdf)

Statistics Norway (SSB) has been using and contributing to PC-Axis for a long time. We were also was part of developing the Common Nordic Meta Model (CNMM) in early 2000.

In march 2001 we launched our public Statbank service. This was an Oracle database implementing CNMM and a webapplication written in Active Server Pages (ASP). The webapplication was based on the Statistics Denmarks Statbank.

Our Statbank has been a success ever since. After at complete rewrite of the ssb.no website in 2013 the Stabank is the only "channel" to disseminate tables/datasets.

Back in 2011 Statistics Sweden (SCB) developed the .Net version of PxWeb. The solution was split up in severel libraries and SSB contributed with a .Net implementation of the SQL connector to CNMM. The soruce code was hosted in subversion at Assembla.com

We also made our first pubic API for Statbank in 2013 based on some of these .Net libraries. But this API only exposed a small part of the Statbank.

However our Statbank struggled to keep up with technical debt and around 2014 we looked to do some upgrading and decided to make the switch to PxWeb.

### Business case
> Issue to address, problems with current solution (or lack of), etc.

- [x] Move the previous paragraphs to Context chapter?
- [x] Explain business case more, in SSB everybody has to disiminate throught the Statbank

In Statistics Norway we have a disimitation policy that says every table/dataset should be made availible in the Statbank. This requires that the statistical departments provide a minimum of metadata and it makes data easier to find knowing that everything is in the Statbank. On the other hand having a central/common(?) solutions like this demands smooth operation and no bottlenecks. 

We also like to provide as much as possible through public APIs as open data.

### Service reuse

#### General description
There were many reasons for us to choose PxWeb but these are some of the main ones.

##### Open source
Access to source code is essential. PxWeb was not open source at the time we started using it, but as we were a contributing party we already had access to the source code.

To depend on closed source when you have your own developers can be a drawback especially when the software in question has a relative small number of users. On the other hand a small number of users makes it easier to request new features.

Regardless we would probably not have chosen PxWeb without access to the source code. The need to customize beyond the excisting plugins and configurations options were to great.

Starting august 2019 PxWeb is completely open source at https://github.com/statisticssweden/PxWeb

##### Puplic API
PxWeb contains a standalone server called PxWebApi. This was very interesting for us since with this we could expose all the contents of our Statbank. PxWebApi supports custom queries several output formats.

[Documentation and video examples](https://www.ssb.no/en/omssb/tjenester-og-verktoy/api/px-api)

##### Modern Tech
In 2014 PxWeb was still "modern tech" especially compared to our old  solution. Today ASP.NET Web Forms is not so modern, but all of the libraries the webapplication is depending on has in 2020 been ported to the conform to .NET Standard 2.0 and the next generation PxWeb and PxWebApi application are being developed.

##### Collaboration
As mentioned we already had close relations with the Nordics NSOs (NSIs?) from working with the CNMM and the .Net libraries. We also realised that

* it's very difficult to create a complete web solution from scratch when you have few developers
* it's much easier to build and customise something that already exists

There is also an annual "International PX meeting" (prev. Pc-Axis reference group meeting) that we attend.

![PX meeting locations last 28 years](px-meetings.png)
Source: [Welcome presentation 2019](https://www.scb.se/contentassets/c6c00c769d874282a5188eace748820b/1-201909xx-welcome-asaarrhenscb.pdf)


In the meeting in Copenhagen 2014 we announced that we would switch to PxWeb.

From arround 2015 the Norwegian og Swedish developers have had weekly short Google Hangouts every friday. These meetings contain

* information sharing, what we are working on locally
* discussion of new features
* problem solving, eg. bugs, performance issues
* feedback from users on the forum

There has also been a few trips to in SCBs offices in Örebro and Stockholm and visits from SCB to our offices in Oslo and Kongsvinger.
Some of these meetings have been pure technical where we do big code merges.

To get most out out the collaboration the social element is key.

##### Launch
To play safe we split the launch in to parts
* PxWebApi was launched in May 2016 as a new application
* PxWeb was launched in January 2018 replacing our StatbankWeb

![PxWebApi launch 2016](pxwebapi-launch.jpg)

#### As-Is and To-Do architectures

- [x] expand on this

During 2020 all the PxFramework libraries in the illustration below where ported to .Net Standard 2.0 and published on NuGet https://www.nuget.org/profiles/pc-axis 

![PxWeb future](pxweb-tobe-arch.png)
Source: [PxWeb 2020 presentation](https://www.scb.se/globalassets/vara-tjanster/px-programmen/pxweb_2020v2_micke-petros.pdf)

The nice thing about having the libraries in .Net Standard 2.0 is that they can be used in both Windows-only and cross-platform framworks.

* .Net Framwork 4.6+
* .Net Core 2.0+
* .Net 5

This was the first step in making PxWeb a cross-platform web application.

The current PxWeb ASP.NET application (2020 v2, released 18. January 2021) is still using .Net Framework 4.6 which is a Windows-only platform, but the libraries are .Net standard.

A cross-platform ASP.NET Core version of the PxWebApi application was planned for 2020 in Statistics Sweden but has been postponed.

The source code for each library is also availible at https://github.com/statisticssweden/ 

Complete list of .Net Standard 2.0 libraries:
* PCAxis.Common
* PCAxis.Core
* PCAxis.Encryption
* PCAxis.Excel
* PCAxis.Html5Table
* PCAxis.Menu
* PCAxis.Menu.MsSqlDatamodelMenu
* PCAxis.Menu.OracleDatamodelMenu
* PCAxis.Metadata
* PCAxis.PX.Core
* PCAxis.PxExtend
* PCAxis.Query
* PCAxis.Sdmx
* PCAxis.Serializers.JsonStat
* PCAxis.Serializers.JsonStat2
* PCAxis.Sql
* PX.Serializers.Json
* PXWeb.SavedQuery.MsSql
* PXWeb.SavedQuery.Oracle



#### Technical details
##### JSON-stat
One of our other contributions to PxWeb has been implementation of the  JSON-stat Dataset output format. I was the format we chose for our first api i 2013 and both JSON-stat v1.2 and 2.0 are available in PxWeb.

* https://json-stat.org/

In the future we like to improve this implementation with more metadata and also implement JSON-stat Collections

Example showing Consumer Price Index 12-month rate (per cent) as JSON-stat
```javascript
{
    "class": "dataset",
    "label": "03013: Consumer Price Index, by contents and month",
    "source": "Statistics Norway",
    "updated": "2020-08-10T06:00:00Z",
    "id": [
        "ContentsCode",
        "Tid"
    ],
    "size": [
        1,
        1
    ],
    "dimension": {
        "ContentsCode": {
            "label": "contents",
            "category": {
                "index": {
                    "Tolvmanedersendring": 0
                },
                "label": {
                    "Tolvmanedersendring": "12-month rate (per cent)"
                },
                "unit": {
                    "Tolvmanedersendring": {
                        "base": "per cent",
                        "decimals": 1
                    }
                }
            }
        },
        "Tid": {
            "label": "month",
            "category": {
                "index": {
                    "2020M07": 0
                },
                "label": {
                    "2020M07": "2020M07"
                }
            }
        }
    },
    "value": [
        1.3
    ],
    "role": {
        "time": [
            "Tid"
        ],
        "metric": [
            "ContentsCode"
        ]
    },
    "version": "2.0"
}
```


#### Organizational impact
> Integration of the service in the process flow.

The main organizational impact is rather technical. Our previous application (from Statitics Denmark) and PxWeb are rather similar from an enduser standpoint. So our gratest benefit was removal of technical dept. Secondly moving to more modern technology made it easier to further develop our website.  

#### Project management
As mentioned in the [general description](#launch) we split the launch in two. 
Both launches was done by our small team of developers already responsible for the entire Statbank solution.
They have long experience working as a Scrum team, and for the first launch it was just a matter of prioritizing the new tasks in the current workflow.

For the second lauch the team was included in a larger project (Kostra). The team had the task of finalizing PxWeb two months prior the main prosject lauch, which they did. The main project was large with three seperate developer teams and a deadline that could not be moved. 

#### Other aspects (e.g. financial)
#### Results achieved

- [x] opensourcing - I3S facilitator for "speeding" the process
- [x] cross-plattform libraries

To focus on the achievments during this I3S project we would mention these

##### Web Content Accessibility Guidelines (WCAG)
During 2019 and 2020 Statistics Norway took the leed role in making PxWeb meet the WCAG 2.0 requirements. Most of this was made availible i PxWeb 2020 v2 and more is comming in future versions.

##### Open Source
PxWeb was made open source under the Apache 2.0 licence in August 2019. It's avilible at https://github.com/statisticssweden/PxWeb

##### Cross-platform
During 2020 all the PxFramework libraries mentioned in [As-Is and To-Do architectures](#as-is-and-to-do-architectures) where ported to .Net Standard 2.0 and published on NuGet https://www.nuget.org/profiles/pc-axis 

## 4. Lessons learned

### Problems encountered
- [ ] containerizing windows web applications. (Maybe this is material for the Blueprint?)
### Missing functionalities
### General feedback
- [ ] learning cloud and container technologies. (Maybe this is material for the Blueprint?)

## 5. Conclusions and next steps
