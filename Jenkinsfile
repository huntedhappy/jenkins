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
                    dockerImage = docker.build registry + “:$BUILD_NUMBER”
                }
            }
        }
        stage(‘Push Image to Docker Hub ‘) {
            steps{
                script {
                    docker.withRegistry( ‘’, registryCredential ) {
                        dockerImage.push()
                        dockerImage.push(‘latest’)
                    }
                }
            }
         }
    }
}