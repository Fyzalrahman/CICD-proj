pipeline {
    agent any
    tools {
        maven 'MAVEN_PATH'
    } // hi
    environment {
       Cred = credentials("DockerCred")
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
              sh 'mv target/myweb*.war target/newapp.war'
            }
        }
        stage("Build Docker Image"){
            steps{
              sh 'sudo docker build -t fyzalrahman/myweb:0.0.2 .'
            }
        }
        stage("Docker Image Push"){
            steps{
              sh 'sudo docker login -u $Cred_USR -p $Cred_PSW '
              sh 'sudo docker push fyzalrahman/myweb:0.0.2'
            }
        }
        stage("Remove Docker Image"){
            steps{
              sh 'sudo docker rmi fyzalrahman/myweb:0.0.2 '
            }
        }
        stage("Docker Container Deployment"){
            steps{
              sh 'sudo docker run -itd -p 8090:8080 --name myweb_devproj fyzalrahman/myweb:0.0.2'
            }
        }
    }
}
