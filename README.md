# Jenkins CI/CD Pipeline with Stage View

## What this project does
Sets up a Jenkins CI/CD pipeline to automatically install dependencies, test, and dockerize a Python Flask app whenever a build is triggered. Pipeline stages are visualized using Jenkins' built-in Pipeline Stage View.

## Note on Blue Ocean
This project originally called for Jenkins Blue Ocean as the UI layer. Blue Ocean is largely deprecated and incompatible with modern Jenkins and current plugin versions. Pipeline Stage View is the current industry standard and is what this project uses instead.

## Tech Stack
- Python + Flask: the app
- pytest: testing
- Docker: containerization
- Jenkins + Pipeline Stage View: the pipeline
- Custom Jenkins Docker image: to include Python and Docker CLI

## Pipeline Stages
1. **Install:** installs Python dependencies via pip
2. **Test:** runs pytest to verify the app works
3. **Docker Build:** builds a Docker image of the app

## How to run locally

### Build the custom Jenkins image
docker build -t jenkins-python -f Dockerfile.jenkins .

### Run Jenkins
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkins-python

### Fix Docker socket permissions
docker exec -u root $(docker ps -q) chmod 666 /var/run/docker.sock

### Run the app after a successful pipeline build
docker run -p 5000:5000 flask-jenkins-app
