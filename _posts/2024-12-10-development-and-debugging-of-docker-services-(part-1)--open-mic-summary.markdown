---
title:  "Development and Debugging of Docker Services (part 1)"
categories: [Open Mic Session, Open Mic]
excerpt: "First in a two-part practical series on developing and debugging with Docker Compose."
---

On Friday 29 November 2024 speaker [Miroslav Blaško](https://kbss.felk.cvut.cz/web/team#miroslav-blaško) held an Open Mic session with the topic \"Development and Debugging of Docker Services (part 1)\". Video and presentation included.

{% include video id="PEvVRG93--4" provider="youtube" %}


##### The abstract

The talk introduced alternative ways of developing Docker services that are orchestrated using Docker Compose. 

When dealing with a large number of interdependent Docker services, it is usually complicated to develop individual services. Instead of running all the dependent services from IDE separately, we elaborate on the idea of reusing the orchestration provided by the Docker Compose setup. Two major alternative solutions to address this use case were introduced. The first solution was explained in detail and showcased through an example Docker Compose setup. The second solution will be explained in the following talk, where it will be compared to the first one.

{% include figure image_path="assets/images/openmics/2024-11-29-example-execution-of-docker-compose-setup.png" alt="Example execution of docker-compose setup" %}

The presentation slides are available [at this link](https://drive.google.com/file/d/11FcQ7jPQDflIdCP_9FVMB48J5zPkMjal/view?usp=sharing).


Further reading:
* [Docker Compose – Use multiple Compose files](https://docs.docker.com/compose/how-tos/multiple-compose-files/)
* [Record Manager UI - Keycloak Authorization Deployment](https://github.com/kbss-cvut/record-manager-ui/tree/main/deploy/keycloak-auth)
