# Declarative-Pipeline-Script-for-Build-and-Deployment-for-Pipeline-Job-using-Jenkins-Master-Slave
This project demonstrates a complete CI/CD pipeline automation for a Java Web Application using Jenkins Declarative Pipeline, configured in a Master–Slave architecture.
The pipeline automates the process of fetching source code from GitHub, building and testing the application with Maven, performing code quality checks with SonarQube, uploading the generated build artifact to Nexus Repository, and deploying the final WAR file to Apache Tomcat through a deploy slave.

The setup simulates a real-time enterprise DevOps workflow used by organizations to ensure smooth, automated, and continuous delivery of software.

🚀 Tools & Technologies Used
Tool	Purpose
Jenkins (Master–Slave Architecture)	Automation server to orchestrate the entire CI/CD process
GitHub	Source code management and version control
Maven	Build automation and dependency management
SonarQube	Code quality and security analysis
Nexus Repository Manager	Artifact storage and version management
Apache Tomcat	Application server to host and deploy the WAR file
Linux (EC2 Instances)	Environment to host Jenkins master and slave nodes

Pipeline Flow
1. Build Job (on Build-Slave)
Stages:

Clone the Repository

Jenkins pulls the latest source code from the GitHub repository.

Validate and Compile the Code

Maven compiles the code and checks for syntax or build errors.

Test the Code

Runs unit tests using the Maven Surefire plugin.

Quality Check and Security Analysis

Executes SonarQube analysis using sonar-maven-plugin.

Sends the code metrics to the SonarQube server for review.

Generate Build Artifact

Packages the code into a .war file using Maven (mvn clean package).

Upload Artifact to Nexus

The generated WAR file is uploaded to the Nexus Repository Manager.

Trigger Deploy Job

Automatically triggers the Deploy pipeline upon successful upload.

2. Deploy Job (on Deploy-Slave)
Stages:

Download the Artifact

Fetches the WAR file from the Nexus repository using wget.

Deploy the Artifact

Deploys the WAR to Apache Tomcat server using Jenkins Deploy to Container Plugin.
