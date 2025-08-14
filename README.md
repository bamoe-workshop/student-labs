# IBM Business Automation Manager Open Editions (IBM BAMOE) Workshop (WB420G) - Student Labs

# Overview
This repository includes all labs created by the student.

# Setting up for your labs
In order to have a place to put the labs that you work on during the training, you will need to create your own branch of the repository.  It is recommended to use your IBMid as your branch name.  If you don't have an IBMid, you can request one at [Create an IBMid](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776).

Be sure to select a unique name, such as your name (no spaces).  In a terminal window:

```shell
cd /home/ibmuser/bamoe-workshop/student-labs
git checkout -b IBMid
git push --set-upstream origin IBMid
```

Now, this repository will be the place that you create all your labs for the training.  

## Building & Deploying Student Labs
In order to be able to build each lab as a container image and automatically push this to the OpenShift cluster, you must be logged into Docker.  You must also set the OpenShift project (namespace) in order for your lab projects to be pushed to the correct location:

To login to Docker, from a command prompt enter:

```shell
	~/docker-login.sh
	oc project bamoe-student-labs
```

## Guidelines
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

Common commands at the root project or entire repository level include:

- ***mvn clean install** - This command will build the project's standalone JAR files, in order to be able to be run using Quarkus Dev Mode:  `mvn clean quarkus:dev -Pdev`.  No container iamge is created during this phase.

- ***mvn clean package -Pdocker** - This command will build the docker container image and push it to the local docker registry.  Use the project's `docker-compose.yml` file in order to deploy the container image to your local Docker.

- ***mvn clean package -Popenshift** - This command will build and automatically deploy the container image to OpenShift, creating it's pods, services, and routes automatically.


> **_TIP:_** The location for which you run Maven commands determines the behavior.  Commands entered at the root of the entire student lab repository will apply to all projects within that repository, whereas commands entered at the root of each sub-module (project) will only apply to that project.  

