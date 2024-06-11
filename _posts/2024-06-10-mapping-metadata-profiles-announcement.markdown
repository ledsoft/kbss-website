---
title: "Upcoming Open Mic - Mapping Various Metadata Profiles to DCAT Family"
categories: [Open Mic Announcement, Open Mic]
---
The Open mic session starts on Friday 14th June 2024 at 10:30 at [this link](https://meet.jit.si/open-mic-kbss). The speaker [Michal Med](https://kbss.felk.cvut.cz/web/team#michal-med) focuses on various metadata profiles and their mapping to the European application profile of the Data Catalogue Vocabulary (DCAT), which is mandatory to share metadata in the European Union. 

##### Abstract
Metadata are the informational documents about the data or other resources. They usually contain basic infomration about the content of the resource, its origin, information about the author or custodian including the contact, conditions for the usage of the data and also qualitative and/or quantitative properties. They are mostly used for discoverability of the resources in the catalogues, statistics and qualitative or quantitative evaluation. Among various domains, based on the purpose of the metadata and characteristics of the resources, there are also various metadata profiles, containing different types of information and having different structures, based mostly on the purpose to which they were made and used.
The problem occures, when metadata, traditionally published in the domain specific profile (e.g. ISO 19139 family [1] for spatial data or DataCite [2] for scientific data) have a legislative obligation [3,4] to be published in the metadata catalogues using another metadata profile, such as DCAT-AP [5] for European data catalogues or DCAT-AP-CZ [6] for open data.
Then, we need to find a functional mapping between the profiles, without the loss of information and also its meaning. In the speech we analyse three families of metadata profiles -- ISO 19139 for spatial data and services, DataCite for scientific data an resources and DCAT-AP for publication and discoverability of data in European infrasructures and open data -- try to create some functional mapping between them leading to the convertability of various profiles with focus on reusing existing ontologies and respecting principles of linked open (meta)data.
It is important to mention also in the abstract, that some functional mapping between profiles already exist, namely GeoDCAT-AP [7] for conversion between ISO 19139 metadata and DCAT-AP and CiteDCAT [8,9] to conform DCAT-AP from DataCite oriented metadata. The mappings has their problems with functional extensions, such as INSPIRE metadata profile [10] or Czech national metadata profile [11] extending ISO 19139 metadata or DCAT-AP-CZ extending DCAT-AP and also with version compatibility of particular mappings, where DCAT-AP-CZ extends DCAT-AP in version 3.0, while GeoDCAT maps metadata properties to the DCAT-AP 2.0.1 etc.
All these problems are analysed and addressed in the presentation, concluding to the set of steps that must be done to fulfil the legislative obligations and keep the metadata useful at the place where they are used now at the same time.


##### Further reading:
1. [ISO/TS 19139-1:2019, an ISO standard for Geographic infomration - XML schema implementation](https://www.iso.org/standard/67253.html)
1. [DataCite Metadata Schema Documentation for the Publication and Citation of Research Data and other Research Outputs](https://datacite-metadata-schema.readthedocs.io/en/4.5/)
1. [Law no. 106/1999 Coll., about the free access to the information (in Czech language)](https://www.e-sbirka.cz/sb/1999/106/2024-01-01?f=106%2F1999&zalozka=text)
1. [Commission Implementing Regulation (EU) 2023/138 of 21 December 2022 laying down a list of specific high-value datasets and the arrangements for their publication and re-use (Text with EEA relevance)](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj?locale=cs#)
1. [DCAT-AP 3.0](https://semiceu.github.io/DCAT-AP/releases/3.0.0/)
1. [DCAT-AP-CZ -- Czech extension of DCAT-AP 3.0 (in Czech language)](https://ofn.gov.cz/dcat-ap-cz-rozhran%C3%AD-katalog%C5%AF-otev%C5%99en%C3%BDch-dat/2024-05-28/)
1. [GeoDCAT-AP version 2.0.0 (draft)](https://semiceu.github.io/GeoDCAT-AP/drafts/latest/)
1. [CiteDCAT-AP Vocabulary](https://lov.linkeddata.es/dataset/lov/vocabs/citedcat)
1. [DataCite to DCAT-AP Mapping](https://ec-jrc.github.io/datacite-to-dcat-ap/)
1. [Technical Guidance for the implementation of INSPIRE dataset and service metadata basewd on ISO/TC 19139/2007](https://github.com/INSPIRE-MIF/technical-guidelines/blob/main/metadata/metadata-iso19139/metadata-iso19139.pdf)
1. [Czech national metadata profile (Národní metadatový profil ČR v4.2)](https://geoportal.gov.cz/c/document_library/get_file?uuid=368cf4c5-b3c1-4e31-a233-f38987dc715c&groupId=10138)
