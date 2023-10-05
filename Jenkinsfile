pipeline {

    agent any

    environment {
        DOCKER_USERNAME = 'seanghouch'
        APP_NAME = 'nginx'
        IMAGE_TAG = "{$BUILDE_NUMBER}"
        IMAGE_NAME = "${DOCKER_USERNAME}" + "/" + "APP_NAME"
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
                    docker_image = docker.build(${IMAGE_NAME})
                }
            }
        }
    }
    
}
