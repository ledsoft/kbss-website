---
title: "Publishing Standalone JAR to Remote Maven Repository"
categories: [ Tips, Maven ]
excerpt: "Sometimes one may find themselves with a project-less JAR and needs to deploy it to a remote repository. This post describes the deployment process."
---

Imagine you need to use a Java library that is not managed and published using the [Apache Maven](https://maven.apache.org/) ecosystem.
Thus, you end up downloading a JAR file and need to integrate this JAR reliably into your project infrastructure, which of course uses Maven.

The best way of doing this is turning the JAR file into a Maven artifact and referencing it in the project using standard
Maven dependency management. Let's say we downloaded a file called `important-library-1.0.0.jar`. We first need to somehow
determine the Maven coordinates of this file. We could inspect the file, looking for the most specific common package name, using it as
`groupId`, `artifactId` and `version` could be based on the JAR file's name. Note that these are to a large extent arbitrary
(with some exceptions, as will be seen later), but it is good to make them at least somewhat deterministic.

### Using Maven Dependency with System Scope

You could put such an artifact among dependencies in your `pom.xml`, give it a `system` scope and provide a `systemPath` parameter specifying path to the file.
Of course, you would want to use a relative path so that the build configuration works on other stations. The dependency would thus look something like this:

```xml
<dependency>
  <groupId>org.example</groupId>
  <artifactId>important-library</artifactId>
  <version>1.0.0</version>
  <scope>system</scope>
  <systemPath>${project.baseDir}/libs/important-library-1.0.0.jar</systemPath>
</dependency>
```

This strategy is fine if you plan to use the dependency only in a single project, and you do not mind putting the library into
SCM.

### Deploying the Artifact to a Remote Maven Repository

Many organizations maintain their own Maven repository, either because they do not want to undergo the publication process of [Maven Central](https://central.sonatype.com/),
or because they have artifacts that they do not want to share with everyone. It is possible to use a repository manager such as
[Sonatype Nexus](https://www.sonatype.com/products/sonatype-nexus-oss), but if one just needs to get
something quickly up and running, it is sufficient to just use a directory accessible by a Web server (on Debian with Apache2, this
could be a directory in `/var/www`). To publish into such a repository, the [Apache Maven Deploy Plugin](https://maven.apache.org/plugins/maven-deploy-plugin/)
has to be used.

Normally, one would declare a [Maven Wagon](https://maven.apache.org/wagon/index.html) plugin in the project's `pom.xml` and
use the Maven Deploy Plugin in cooperation with Wagon to deploy the artifact (Wagon and its providers take care of the actual
data transfer). This gets trickier when we do not have any `pom.xml`.

[Maven guide](https://maven.apache.org/guides/mini/guide-3rd-party-jars-remote.html) on deploying JARs to remote repository
mentions that one needs to have a corresponding Wagon provider in `${maven.home}/lib`. However, by default, Maven comes with only the `file` and `http`
Wagon providers. If we want to deploy using SCP (which is probably the most common way for a remote repository), Maven will complain because it
does not have a suitable Wagon provider for this. Therefore, we need to download the corresponding provider JAR's and manually place them into Maven home.

The following is a complete guide to setting up and deploying JAR files to a remote repository using Maven and Wagon over SCP:

- Find out where your `${maven.home}` is. It is usually the installation directory of Maven. Easiest way is to run `mvn -v` and look for the home directory in the output.

{% include figure image_path="assets/images/posts/2024-04-25-maven-home.png" alt="Output of the 'mvn -v' command." %}

- Download the [Wagon SSH External](https://central.sonatype.com/artifact/org.apache.maven.wagon/wagon-ssh-external/) and [Wagon SSH Common](https://central.sonatype.com/artifact/org.apache.maven.wagon/wagon-ssh-common) JARs from Maven Central and place them in `${maven.home}/lib`.
  You should download version matching the version of the Wagon providers already present in `${maven.home}/lib`.
- Set up SCP connection to your target server using SSH keys (the deployment does not work with username/password combination).
- Put configuration of the SCP connection into `${user.home}/.m2/settings.xml`. The configuration may look something like:

```xml
<server>
    <id>server-id</id>
    <username>my-username</username>
    <privateKey>${user.home}/.ssh/id_rsa</privateKey>
</server>
```
- Now you can deploy the artifact using Apache Maven Deploy Plugin:

```shell
mvn deploy:deploy-file -Dfile=important-library-1.0.0.jar -DgroupId=org.example -DartifactId=important-library -Dversion=1.0.0 -Dpackaging=jar -DrepositoryId=server-id -Durl=scpexe://my-remote-server.com:/path/to/maven/repository
```

Some additional notes:
- The `repositoryId` parameter in the deployment call must match the server id in `settings.xml`.
- We assume SCP is installed on the calling system. Wagon SSH External will use this existing SCP installation.
- The JAR file's name should correspond to the artifactId and version.


### What Does Not Work?

You may be tempted to skip the hassle with Wagon, copy the JAR file directly to the server and install it using the
[Maven Install Plugin](https://maven.apache.org/plugins/maven-install-plugin/).
However, this will not work because the Maven Install Plugin does not generate the `maven-metadata.xml` file and Maven will
not be able to use such an artifact.

## Conclusion

Using libraries that are distributed outside the Apache Maven ecosystem is possible in multiple ways. But if the library
is expected to be used by multiple projects, it makes sense to publish it to a remote repository. This post has provided
steps to accomplish this.

Hopefully, someone (maybe me in a couple of months/years) finds this useful.
