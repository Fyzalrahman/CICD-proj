pipeline {
    agent any
    tools {
        maven "MAVEN_PATH"
    }    // For Maven path Either tools or environment variable is required
    environment {
        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
    }
    stages {
        stage("SCM Checkout"){
            steps{
               git credentialsId: 'DockerCred', url: 'https://github.com/Fyzalrahman/CICD-proj'
            }
        }
        stage("Compile Package"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("Build Docker Image"){
            steps{
              sh 'docker build -t fyzalrahman/myweb:0.0.2 .'
            }
        }
        stage("Docker Image Push"){
            steps{
              sh 'docker login -u -p '
              sh 'docker '
            }
        }
    }
}
