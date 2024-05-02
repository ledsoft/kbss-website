---
title:  "Git Team Workflow"
categories: [Open Mic Session, Open Mic]
excerpt: "This two-part presentation discussed best practices for using Git in a team project."
---

On Friday 1st and Friday 8th March our guest speaker [Petr Aubrecht](https://www.linkedin.com/in/petraubrecht/) held an Open Mic session with the topic \"Git Team Workflow\".

{% include video id="YCl4ppjRC1U" provider="youtube" %}

The video contains only the main presnetation content, the whole discussion and Q&A section was cut off, because the video itself was too long (over 2.5 hours of raw material). The video is cut into the sections by the topics.

##### The abstract

Git is ubiquitous in software development nowadays, but using it differs quite significantly when working alone and when working in a team. Beginners may
struggle in finding the right workflow for working with Git in a team.

This presentation provides some best practices learnt over years by an industry veteran with experience with working in development teams on
various kinds of projects, both closed source and open source, including community-driven projects like
[Jakarta EE specification implementations](https://github.com/eclipse-ee4j/glassfish-concurro).

Some key takeaways:
- What gets to Git stays in Git, it just may be harder to find
- Git commit messages should be meaningful
- Feature branches should be short-lived to prevent issues with synchronizing them with the main branch
  - If they are long-lived, synchronize with main often
- Developers should strive for a clean history, `git rebase` is helpful (and prevents railway station-type of history)
- It is a good idea to squash work-in-progress commits
- For small teams, it may be a good idea to just work on the same repository without PRs at all (but set up CI first so that pushes that break stuff are found quickly)

{% include figure image_path="https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=1450" alt="Git workflow example." caption="Git workflow example. Source: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow" %}

The presentation slides are available [at this link](https://drive.google.com/file/d/1ReVafF_iYU2PQ71Vbu42-teQErLeFB7X/view?usp=sharing).

##### About the Speaker

[Petr Aubrecht](https://www.linkedin.com/in/petraubrecht/) is a software developer and team leader with decades of experience. Starting out in academia (he holds a [PhD](https://home.asoftware.cz/school/disertace/disertation1.pdf) in Artificial intelligence and biocybernetics),
he later transferred into industry, where he has held several key developer positions, including senior software engineer, team lead etc. A keen Java developer
and [Jakarta EE](https://jakarta.ee/) (Java EE) enthusiast, he has recently taken his love for Jakarta EE to the next level by joining the team developing one of the
Jakarta EE application servers - [Payara](https://www.payara.fish/).

Further reading:
* [Pro Git](https://git-scm.com/book/en/v2) - first three chapters are a must for anyone working with Git
* [Atlassian Git workflow tutorial](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

