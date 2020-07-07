# Jenkins
Jenkins is an open-source automation server that is used to automate tasks related to end-to-end software development. Jenkins
can handle building, testing (such as functional testing, integration testing, vulnerability testing), delivering or
deploying software.

Jenkins started as a building and testing automation server (CI) in Java ecosystem and those are the still strongest capabilities of it. However currently it includes builders (mostly as a plugin)  such as Cmake, Rake,Ruby, Python, shell script, MSBuild, Batch Script in addtion to original Ant and Maven builders.

The extendibility is strongest feature of Jenkins and that makes it enterprise level automation software.
Jenkins functionality can be extended easily by using plugins. By using plugins it can be integrated to Bugzilla, Google Code, Jira, Mantis and notification tools such as smtp, Google Calendar, IRC, XMPP, RSS, Twitter, Slack and IDEs like Eclipse, IntelliJ IDEA, Netbeans.

Jenkins support most of the known source control management systems such as Git, CVS, Subversion , Mercurial. Visula Source Safe, AccuRev and etc. Most of those systems can be integrated its build system to fetch the source code automatically.

Jenkins X is extended CI/CD solution for modern applications on Kubernetes. It automates end to end CI/CD pipline for microservices. It creates Dockerfile, helm chart (for deploying and running your application on Kubernetes). It also support Environment Promotion via GitOps whihc provides differetn environmetns for Staging and Production (or any enviroment that is needed). Each environment is mapped to a namespace in Kubernetes so they are isolated and can be managed independently. Enviroments can have own git repository to store all specific configurations. 

## How to use 
Jenkins can be installed as a Docker image or as a web application archive (war). 
RHEL/Centos

```
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
sudo yum upgrade
sudo yum install jenkins java-1.8.0-openjdk-devel

sudo systemctl start jenkins
```
After installation it can be accessed  through 

```
http://localhost:8080 

```
Or address/ip of your hosting machine.

After installation you may need to add plugins via Jenkins web interface.

Any CI pipeline an be created via web interface or by using Jenkins file


For Python
```
pipeline {
    agent { docker { image 'python:3.5.1' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
```
For Go 

```
pipeline {
    agent { docker { image 'golang' } }
    stages {
        stage('build') {
            steps {
                sh 'go version'
            }
        }
    }
}
```

Example jenkins file can be reached from  Jenkins.io 



## Resources 

Example:
- [](https://aws.amazon.com/blogs/opensource/continuous-integration-using-jenkins-and-hashicorp-terraform-on-amazon-eks/)
    - This tutorial is about Jenkins Deployment in AWS


## Pain Points 
Some Jenkins plugin are lack of staiblity so they can cause to Jenkins break.




