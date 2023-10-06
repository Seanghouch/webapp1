pipeline {

    agent any

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
        agent {
            docker {
                image 'gradle:8.2.0-jdk17-alpine'
                // Run the container on the node specified at the
                // top-level of the Pipeline, in the same workspace,
                // rather than on a new node entirely:
                reuseNode true
            }
        }
        steps {
            sh 'gradle --version'
        }
        stage('Build Docker Image'){
            steps{
                script{
                    checkout scm
                    sh 'docker build -t custom-nginx .'
                }
            }
        }
    }
    
}
