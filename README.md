# Dynamic-Versioning-on-Java-Maven-CI-CD-with-Jenkins-Docker-and-git
# Pipeline README

This repository contains a Jenkins pipeline script that automates the CI/CD process for a Java application. The pipeline consists of several stages, each with specific steps that are executed.

## Prerequisites

*   Jenkins should be set up and configured to run this pipeline.

## Pipeline Description

### Stage: increment version

*   This stage increments the application version by parsing the current version from the `pom.xml` file and updating it.
*   The updated version is stored in the `IMAGE_NAME` environment variable in the format `version-BUILD_NUMBER`.

### Stage: build app

*   This stage cleans and builds the application using Maven.

### Stage: build image

*   This stage builds a Docker image for the application and pushes it to the Docker Hub repository.
*   Docker credentials (username and password) are required and stored securely in Jenkins.
*   The Docker image is tagged with the `IMAGE_NAME` constructed in the previous stage.

### Stage: deploy

*   This stage deploys the Docker image to a specified target environment. The actual deployment steps are not defined in this pipeline and need to be added by the user.

### Stage: commit version update

*   This stage commits the updated version back to the Git repository.
*   Git credentials (username and password) are required and stored securely in Jenkins.
*   The pipeline sets the Git repository's remote URL using the provided credentials.
*   Changes in all files are added, committed with a message, and pushed to the `main` branch.

## Notes

*   Ensure that the required Jenkins plugins and tools are installed and configured.
*   Customize the pipeline stages, steps, and configurations as per your project requirements.

Feel free to reach out if you have any further questions or need assistance!
