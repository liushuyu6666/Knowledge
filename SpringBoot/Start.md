# Overview
To initiate a Spring Boot project, navigate to the official `Spring Initializr` at https://start.spring.io/. This platform provides engineers with a straightforward approach to commence a new Spring Boot project.  

# Spring Initializr
In the `Spring Initializr`, there are several sections, each of which will be presented in detail.

## Project
The "Project" section in the Spring Initializr specifies the build automation tool and build script options, with three available choices:

* `Gradle - Groovy`: use the Groovy programming language for its build scripts. 
* `Gradle Kotlin`: use the Kotlin programming language for its build scripts.
* `Maven`: use `Maven` as the build automation tool with a `pom.xml` file as build script.

**Build scripts** are files that contain instructions for building, testing, and deploying a software project. They specify the dependencies, plugins, and other configuration needed to build and package your Spring Boot application. The build script for a Spring Boot project is usually located in the project's root directory, with the filename `build.gradle` (for Gradle) or `pom.xml` (for Maven).

## Language
Please select your preferred programming language. Note that Java is the prevailing language.

## Project Metadata
Nothing special, we only need to pay attention to packaging part. 
* `JAR` (Java Archive) packaging: It is a package format that contains compiled Java code, resources, and metadata. It is used for packaging and distributing a standalone Spring application as a single executable file.
* `WAR` (Web Application Archive) packaging: It is a package format used for packaging web applications in Java. It contains compiled Java code, JSP files, HTML pages, JavaScript, CSS files, and other resources. A `WAR` file is intended to be deployed on a web server, such as Apache Tomcat or Jetty. When a `WAR` file is deployed, it is exploded into a directory structure and the web server runs the application.

## Dependencies
Two dependencies will be installed automatically:
1. `spring-boot-starter`
2. `spring-boot-starter-test`

Besides, `org.springframeworkboot:spring-boot-starter-web` is suggested for web application.





