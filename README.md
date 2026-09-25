End-to-End CI/CD Pipeline with Jenkins, GitHub & Maven

Project Overview

This project demonstrates an end-to-end CI/CD pipeline using
Jenkins, GitHub, Maven, and AWS EC2.

Whenever code is pushed to the GitHub repository, a GitHub webhook
triggers Jenkins automatically. Jenkins checks out the latest source
code, builds and tests the Java application using Maven, generates a JAR
artifact, archives the artifact, and sends email notifications for
successful or failed builds.

Technologies Used

Jenkins -- CI/CD automation

GitHub -- Source code management

Maven -- Build and dependency management

Java -- Application development

JUnit -- Unit testing

GitHub Webhooks -- Automatic build triggering

AWS EC2 / Ubuntu -- Jenkins server

Gmail SMTP -- Build notifications

Architecture

Developer
    |
    | git push
    v
GitHub Repository
    |
    | GitHub Webhook
    v
Jenkins on AWS EC2
    |
    | Checkout source code
    v
Maven Build
    |
    +--> Unit Tests
    |
    +--> mvn clean package
    |
    v
JAR Artifact
    |
    | Archive
    v
Jenkins
    |
    +--> SUCCESS Email
    |
    +--> FAILURE Email

Repository

GitHub:
https://github.com/shijoshalom/jenkins_maven

Project Structure

jenkins_maven/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               └── App.java
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── AppTest.java
├── pom.xml
└── README.md

Application

The project contains a simple Java application that prints:

Hello from Jenkins + Maven CI/CD Pipeline!

A JUnit test is also included to verify the application build process.

Jenkins Configuration

The Jenkins job is configured as:

Job Name: jenkins_maven

Source Code Management

SCM: Git

Repository: https://github.com/shijoshalom/jenkins_maven.git

Branch: */main

Build Trigger

Jenkins is configured with:

GitHub hook trigger for GITScm polling

A GitHub webhook sends a POST request to Jenkins whenever code is pushed
to the repository.

Maven Build

The Maven build command is:

mvn clean package

Jenkins uses:

Root POM: pom.xml
Goals and options: clean package

Artifact Archiving

The generated JAR file is archived using:

target/*.jar

The generated artifact is:

jenkins-maven-demo-1.0.jar

GitHub Webhook

The repository is configured with a GitHub push webhook pointing to
Jenkins.

The webhook is configured to trigger on:

Push events

A successful webhook delivery returns:

HTTP 200

This enables the following automated workflow:

GitHub Push → Webhook → Jenkins Build

Build Validation

Successful Build

A successful Jenkins build performs:

Git checkout

Maven compilation

Unit testing

Packaging

JAR generation

Artifact archiving

Expected result:

BUILD SUCCESS
Finished: SUCCESS

Failed Build

The pipeline was also tested with an intentional Java compilation error
to verify Jenkins failure handling.

Expected result:

COMPILATION ERROR
BUILD FAILURE
Finished: FAILURE

After testing, the source code was restored and the final project state
was verified with a successful build.

Email Notifications

Jenkins is configured with Gmail SMTP using:

SMTP Server: smtp.gmail.com
SMTP Port: 587
TLS: Enabled
SMTP Authentication: Enabled

A Google App Password is used for SMTP authentication.

The Jenkins Email Extension plugin is configured with:

Success notification

Failure - Any notification

This allows Jenkins to notify the configured recipient when a build
succeeds or fails.

CI/CD Workflow

The complete pipeline works as follows:

1. Developer pushes code to GitHub
              ↓
2. GitHub sends webhook notification
              ↓
3. Jenkins receives the webhook
              ↓
4. Jenkins checks out the latest code
              ↓
5. Maven executes clean package
              ↓
6. Unit tests are executed
              ↓
7. JAR artifact is generated
              ↓
8. Jenkins archives the JAR
              ↓
9. Email notification is sent

Key Learning Outcomes

Configured Jenkins on an AWS EC2 Ubuntu server

Integrated Jenkins with GitHub

Configured GitHub webhooks

Used Maven for Java builds

Automated unit testing through Jenkins

Archived Maven build artifacts

Tested both successful and failed builds

Configured Jenkins email notifications

Implemented an end-to-end CI workflow

Conclusion

This project demonstrates a complete Jenkins-based CI/CD workflow where
source code changes in GitHub automatically trigger a Maven build in
Jenkins. The pipeline validates the application, generates and archives
the JAR artifact, and provides email notifications for build status..
