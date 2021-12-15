pipeline {
    environment {
        registry = "jenkins-docker-pipeline/my-image"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning Git') {
        steps {
            git 'ssh://git@github.com:huntedhappy/jenkins.git'
        }
    }
        stage('Building Docker Image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":$tag"
                }
            }
        }
    }
}
