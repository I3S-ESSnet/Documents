# Names entity recognition service

**DO**: Insee

**RO**:

**Rank**: 

**Functionalities mapped to the GSBPM**: 7.1. Update output systems

**State of achievement**: prototype available

**Distance to CSPA**: compliant with CSPA principles

**Technical prerequisites**: web platform

**Risks**: -

**Description**: Like many other statistical institutes, Insee manages a list of statistical concept definitions (see https://www.insee.fr/en/information/2565539). These definitions are explicitly referred to in the dissemination products, but Insee produces also a lot of textual content (publications, web pages, research documents and studies) that also refers to the statistical concepts, but without formally linking to them. Establishing such formal links would greatly improve the coherence and discoverability of our products. 
The named-entity recognition (NER) service proposed here aims at automating this task, by using text-mining and natural langage processing techniques in order to extract from a text the occurrences of entities of interest (names, places, events, or more generally concepts in a given knowledge system). A well-known example of such a service is OpenCalais (http://www.opencalais.com/). The NER service would adapt these techniques to the recognition of statistical, economical and social concepts. 
 A specific challenge for this service is multilinguism. This will be addressed by relying on the use of open source standard tools like Apache Stanbol / OpenNLP or, at a lower level, Apache Lucene, which already provide multilingual support.
