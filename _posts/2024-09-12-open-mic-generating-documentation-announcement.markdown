---
title: "Upcoming Open Mic - Generating and Publishing Ontology Documentation"
categories: [Open Mic Announcement, Open Mic]
---
The Open mic session starts on Friday 20th June 2024 at 10:30 at [this link](https://meet.jit.si/open-mic-kbss). The speaker [Michal Med](https://kbss.felk.cvut.cz/web/team#michal-med) introduces his research in the automatic generation and publication of documentation of ontologies. This weeks session follows up the speech from December 2023[1].

##### Abstract
The aforementioned Open Mic session [1] explored various tools for visualization and documentation of ontologies. This session goes further and describes how to create an automatic pipeline, that generates and publishes documentation as the source ontology is published or updated.
In the presentation, we describe the pipeline as we have built it. Pipeline uses Widoco as a tool for generating ontologies. Ontologies are managed in GitHub and the pipeline itself is managed by Jenkins[4]. If the GitHub push is revieved, the webhook sends a payload to whoever listens. We have set up a Jenkins job listening to this webhook and on change, the pipeline regenerates the documentation and publishes it on the server. In the speech, Michal will describe the whole process step by step, discuss the problems and sums up how it works so far. Presentation introduces all necessary steps to add ypur ontology into the aiutomated process of continual documentation generation and publication.
Finaly the presentation focuses also on the future steps to ensure dereferencing of the resources, whisch is not yet solved.

##### Further reading:
1. [Widoco & its alternatives](https://kbss.felk.cvut.cz/web/open-mic-widoco-and-co)
