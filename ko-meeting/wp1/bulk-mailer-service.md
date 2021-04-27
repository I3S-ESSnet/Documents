# Bulk mailer

**DO**: Insee

**RO**:

**Rank**: 

**Functionalities mapped to the GSBPM**:

SPOC is related to the phases *4.3 Run collection* and *7.4 Promote dissemination products* of the GSBPM.

For the 4.3 phase the main uses are :
* announce the opening of a survey collection to respondents
* send a questionnaire to a respondent
* send reminders to non respondents
* reinitialize password mails

For the 7.4 phase the main uses are :
* send notifications of publication to subscribers
* send information letters

**State of achievement**: Version 2.0 available

**Distance to CSPA**: available as a CSPA-available service

**Technical prerequisites**: 

The SPOC service can be called by client applications via a REST web service. The communication between SPOC and the client can use XML or Json.

The communication between SPOC and the mail server is simply using SMTP.

For client identification, SPOC uses a LDAP directory.

SPOC code source is written in Java. It is not yet internationalized nor opensource.

**Risks**: -

**Description**:

SPOC can send mails with the following characteristics :
* configurable sender field
* the content of the mail can be raw text or html
* recipients addresses can be given in cc or cci field
* max. 500 recipients for a mail
* attached documents possible
* individual mail (one mail by recipient) or grouped mail (one mail for all recipients, cc-ed or cci-ed; content not configurable; same attached documents for all recipients)

SPOC can use templates with configurable fields in the object and content.

A report is available after the mailing.

Check before mailing :
* syntax of the recipients addresses
* size of the mail (attached documents included)
* number of recipients for a mailing (max. 500)

**Planned evolutions**:

* Logging of the mailing, with a GUI for consultation.
* Design of standard reusable templates
* Management of "unknow address" error code
