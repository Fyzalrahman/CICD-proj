pipeline {
    agent any
    environment {
        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
    }
    stages {
        stage("SCM Checkout"){
            steps{
               sh 'https://github.com/ravdy/hello-world.git'
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
