pipeline {
    agent any
    stages {
        stage('Clean WP'){
            steps{
                cleanWs()
            }
            steps{
                sh 'docker --version'
            }
        }
        stage('Build') {
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
               
                sh 'docker --version'
            }
        }
    }
}
