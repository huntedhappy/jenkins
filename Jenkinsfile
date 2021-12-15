pipeline {
    environment {
        registry = “bkshashi9/webapp”
        registryCredential = ‘dockerhub’
        dockerImage = ‘’
    }
    agent any
    stages {
        stage(‘Cloning Git’) {
        steps {
            git ‘https://github.com/huntedhappy/jenkins.git’
        }
    }
        stage(‘Building Docker Image’) {
            steps{
                script {
                    dockerImage = docker.build registry + “:$tag”
                }
            }
        }
    }
}