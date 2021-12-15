pipeline {
    environment {
        registry = "jenkins-docker-pipeline/my-image"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning Git') {
            steps{
                checkout scm
            }
        }
        stage('Building Docker Image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":$tag"
                }
            }
        }
        stage("install helm"){
            steps {
                sh 'wget https://get.helm.sh/helm-v3.6.1-linux-amd64.tar.gz'
                sh 'ls -a'
                sh 'tar -xvzf helm-v3.6.1-linux-amd64.tar.gz'
                sh 'cp linux-amd64/helm /usr/bin'
                sh 'helm version'
            }
        }	
        stage('Run Helm') {
            steps {
                script {      
                    container('helm') {
                        sh "helm ls"
                    }
                } 
            }
        }        
    }
}
