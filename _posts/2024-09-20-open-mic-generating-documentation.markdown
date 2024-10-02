---
title: "Generating and Publishing Ontology Documentation"
categories: [Open Mic Session, Open Mic]
---
The Open mic session took place on Friday 20th June 2024. The speaker [Michal Med](https://kbss.felk.cvut.cz/web/team#michal-med) introduced his research in the automatic generation and publication of documentation of ontologies. This session follows up the speech from December 2023[1]. The whole speech, including the discussion, was as usual recorded. The video is available here:

{% include video id="Pu-T6jjOrVE" provider="youtube" %}

##### Problem?
The speech is trying to get the solution to the following problem: **how to automatically update the ontology documentation on the web when the ontology is updated?**

{% include figure image_path="/assets/images/posts/2024-09-20-problem.png" alt="Problem definition." %}{: .post-image }

There are plenty of options on how to do this, but most of them have to solve following four questions:
1) Where to store the ontology/ies?
2) How to find out that the ontology changed?
3) How to (re)generate the documentation with as much variables recieved from the ontology?
4) How to publish it on server?

##### Solution!
As written before, there is definitely more ways on how to solve the problem. Proposed solution is pictured in the following diagram:

{% include figure image_path="/assets/images/posts/2024-09-20-solution.png" alt="Solution diagram." %}{: .post-image }

We propose using GitHub[2] to store the ontology and then use a webhook to send information about the change and also some of the metadata. On the other side is Jenkins[3] handling the webhook payload. There are still some variables passed on through metadata configuration file or written in the pipeline by hand, but most of them could be passed on from the webhook payload, or using the ontology properties. This will be investigated in more detaile in the future work. Jenkins then runs Widoco[4] with the variables extracted from webhook payload and generates documentation on the server, where the Jenkins is running. The last step is deployment on the server. Jenkins pipeline copies all the files to the publication server and changes the ownership of the files to be readable. It also checks the current version of the ontology nad recreates the symlink if needed. Last manual work for the NEW ontologies is to add aliases and rewrite conditions in the Apache HTTP server[5] configuration, so the documentation web pages are published.

##### Future?
The described solution is working (!!!), but in the discussion that followed the presentation (see the record) were made some suggestions to make it work even better. 

1. Webhook vs. GitHub action -- instead of GitHub webhook, there may be better solution to call a GitHub action on merging pull request in the GitHub repository with ontology. Anyway, ther must be something ran on the server to generate the documentation, which requiers either enabling running Jenkins, or setting up some service on the server, which handles generating the ontology documentation there.
1. Metadata config file vs. ontology metadata -- the main reason for using standalone configuration file with metadata for generating documentation is location of files with static text for documentation sections. For all other metadata it would be easier and more effective to include metadata into the ontology itself[6], which is also recommended in the Widoco documentation. 
1. One Jenkins Job to rule them all -- the current setup is counting on one ontology file per GitHub repository. If we are able to handle repository and branch information through the webhook payload, we can serve multiple repositories with just one Jenkins job. Next step is to handle more ontologies present in one repository, but this step requires setting and following methodological rules while creating repositories.
1. Automatization of Apache configuration -- this is the problem only for the first registration of ontology. For the documentation to be published, RewriteCond and Aliases for the URL and file locations must be added to the Apache configuration file. As Apache suports imports, configuration file may be created automatically from pipeline and then imported from Apache config file.


The presentation slides are available by clicking [this link.](https://drive.google.com/file/d/1pvEhwbn7AhghA8-EJcNDB_q2l2jeTa4L/view?usp=sharing)

##### Further reading:
1. [Widoco & its alternatives](https://kbss.felk.cvut.cz/web/open-mic-widoco-and-co)
2. [Github](https://www.github.com)
3. [Jenkins](https://www.jenkins.io)
4. [Widoco](https://github.com/dgarijo/Widoco)
5. [Apache HTTP server project](http://www.apache.org)
6. [Metadata usage in WIDOCO](https://github.com/dgarijo/Widoco/blob/master/doc/metadataGuide/guide.md)