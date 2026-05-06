## Standard Operating Procedure

### Prerequisites
- Docker installed on your machine

### Running Jenkins
1. Build the custom Jenkins image:
   docker build -t jenkins-python -f Dockerfile.jenkins .

2. Run Jenkins:
   docker run -p 8080:8080 -p 50000:50000 \
     -v jenkins_home:/var/jenkins_home \
     -v /var/run/docker.sock:/var/run/docker.sock \
     jenkins-python

3. Fix Docker socket permissions (run in a second terminal):
   docker exec -u root $(docker ps -q) chmod 666 /var/run/docker.sock

4. Open Jenkins at http://localhost:8080

### Connecting to GitHub
1. Create a Pipeline job in Jenkins
2. Set Definition to "Pipeline script from SCM"
3. Set SCM to Git and enter your repo URL
4. Set branch to */main
5. Click Save then Build Now

### Running the App
After a successful pipeline build, run the Docker image:
   docker run -p 5000:5000 flask-jenkins-app

Visit http://localhost:5000 to see the app running.