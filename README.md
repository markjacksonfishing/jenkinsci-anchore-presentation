# Jenkinsci Anchore Presentation
This repository is the home to the code for the presentation titled Securing your Jenkins CI CD Container Pipeline with Anchore

## Details
This is an example for building a Node application using Jenkins. It includes

- A simple Hello World HTTP server in Node
- `Dockerfile` for building the Docker image with the application
- `Jenkinsfile` that defines the pipeline for the build process and analysis of the Docker image using Anchore plugin

## Instructions
Install and Configure Jenkins
This example runs Jenkins in a Docker container. It employs jenkinsci/blueocean Docker image since the image contains the current LTS release of Jenkins along with most of the required plugins (Blue Ocean, Pipeline and Docker). Docker must be installed on your operating system before you can start using it. For more information about prerequisites and installation options refer to the official docs at https://jenkins.io/doc/book/installing/#docker

$ docker run -u root -d --name jenkins -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v jenkins-data:/var/jenkins_home jenkinsci/blueocean

Follow the steps in https://jenkins.io/doc/book/installing/#setup-wizard to access the Jenkins instance and complete the setup

Install Anchore Container Image Scanner plugin
Go to Manage Jenkins->Plugin Manager->available tab, search and select Anchore Container Image Scanner, click Download now and install after restart.

[plugin-install](/images/img_1-1024x864.png)

Select Restart checkbox to restart Jenkins instance and activate the plugin

Login to the Jenkins classic UI and access the Blue Ocean UI by clicking Open Blue Ocean on the left

[open blue ocean](/images/open-blue-ocean-link-1.png)

If your Jenkins instance is new or has no Pipeline projects, then Blue Ocean UI displays a Welcome to Jenkins box with a Create a new Pipeline button. Click the button to start the Pipeline project. If the Blue Ocean UI displays a dashboard view with existing Pipeline projects, click the New Pipeline button on the top right corner.

[new pipeline](/images/img_2-1-1024x864.png)

Select Git from the list of code repositories and enter “https://github.com/markyjackson-taulia/jenkinsci-anchore-presentation” for the Repository URL. Credentials are optional. Click Create Pipeline

Note: The Pipeline project can also be configured to scan and poll a GitHub repository for commits. For instructions, refer to https://jenkins.io/doc/book/blueocean/creating-pipelines/#for-a-repository-on-github

[create pipeline](/images/img_3-2-1024x864.png)

This should start up a new job that immediately transitions to a paused state

