# IBM Business Automation Manager Open Editions (IBM BAMOE) Workshop - Student Labs

# Overview
This repository includes all labs created by the student.

# Setting up for your labs
In order to have a place to put the labs that you work on during the training, you will need to create your own branch of the repository.  It is recommended to use your IBMid as your branch name.  If you don't have an IBMid, you can request one at [Create an IBMid](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776).

Be sure to select a unique name, such as your name (no spaces).  In a terminal window:

```shell
cd /home/bamoe-workshop-student/bamoe-workshop/student-labs
git checkout -b IBMid
git push --set-upstream origin IBMid
```

Now, this repository will be the place that you create all your labs for the training.  \

# Guidelines
Use the supplied [Maven Archetypes](../bamoe-maven/README.md) in order to generate the lab project of your choice.  You can emplly a `multi-module` approach to your labs, creating a project for each appliation and then creating a master `pom.xml` that builds all of them in one step.  For example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

  	<groupId>com.ibm.edu.bamoe.workshop</groupId>
  	<artifactId>student-labs</artifactId>
	<version>1.0.0</version>
	<packaging>pom</packaging>

	<!-- Add a <module> for each lab project you create here -->
	<modules>
	</modules>
</project>
```

You can now run Maven commands either in the root folder or each project's folder.  Any command performed at the root folder level will apply to all
projects.


