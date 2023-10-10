pipeline {

    agent {
        label 'jenkins-agent'
    }

    environment {
        DOCKER_USERNAME = 'seanghouch'
        APP_NAME = 'nginx'
        IMAGE_TAG = "{$BUILDE_NUMBER}"
        IMAGE_NAME = "${DOCKER_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
        VERSION = 1.0
    }

    stages{
        stage('Cleanup Workspace'){
            steps{
                 script{
                    cleanWs()
                }
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    checkout scm
                    sh 'docker --version'
                    sh 'java --version'
                    sh 'docker build -t mywebapp1 .'
                    docker.withRegistry('https://registry.hub.docker.com', REGISTRY_CREDS) {
                        def customImage = docker.build("${IMAGE_NAME}:${env.BUILD_ID}")
                        /* Push the container to the custom Registry */
                        customImage.push()
                    }
                }
            }
        }
    }
    
}
