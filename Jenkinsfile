pipeline {

    agent any

    environment {
        DOCKER_USERNAME = 'seanghouch'
        APP_NAME = 'nginx'
        IMAGE_TAG = "{$BUILDE_NUMBER}"
        IMAGE_NAME = "${DOCKER_USERNAME}" + "/" + "APP_NAME"
        REGISTRY_CREDS = 'dockerhub'
    }

    stages{
        stage('Cleanup Workspace'){
            script{
                cleanWs()
            }
        }
        stage('Checkout SCM'){
             script{
                git credentialsId: 'github',
                url: 'https://github.com/Seanghouch/webapp1.git',
                branch: 'main'
             }   
        }
    }
    
}
