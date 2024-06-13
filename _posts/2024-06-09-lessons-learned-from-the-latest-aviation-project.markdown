---
title: "Lessons Learned from the Last Aviation Project"
categories: [Open Mic Session, Open Mic]
---

On Friday 31st April 2024, our research group leader [Miroslav Blaško](https://kbss.felk.cvut.cz/web/team#miro-blaško) discussed in an open mic session the lessons learned from the latest aviation project, which involved developing an information system for AERO Vodochody AEROSPACE a.s. (AVA). This system aims to collect and process operational data to enhance the safety and reliability of aircraft. A key objective of the operational data is to provide input for failure analysis using the Fault Tree Analysis (FTA) technique.

{% include video id="w9hDa51cQt0" provider="youtube" %}

##### Abstract
The development of an information system for AERO Vodochody AEROSPACE a.s. introduced several new challenges related to using tools developed by KBSS. This presentation details the system architecture and highlights the roles of KBSS tools such as SPipes, SForms, and Record Manager. The system employs Docker Compose for service orchestration and integrates Keycloak for user management. It utilizes Ontotext GraphDB for the database, accessed via the Java OWL persistence framework JOPA. SPipes manages and executes semantic pipelines defined in RDF, while SForms is a JavaScript library that implements data collection based on interactive ontology-based forms. Record Manager is a domain-independent tool for managing records collected by SForms.

The presentation slides are available [at this link](https://drive.google.com/file/d/13Ttky2zWgkeKTwzr-Uljacfc44QgnuO5/view?usp=drive_link).

##### Further reading:
* [SPipes - Engine for Processing Semantic Pipelines Defined in RDF](https://github.com/kbss-cvut/s-forms)
* [SForms - Ontology-based Smart Forms](https://github.com/kbss-cvut/s-forms)
* [Record Manager - Manager of Ontology-based Smart Form Records](https://github.com/kbss-cvut/record-manager-ui)
* [JOPA - Java OWL Persistence API](https://github.com/kbss-cvut/jopa)

