pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'ls -a'
                sh 'docker pull seanghouch/nginx:1.0'
            }
        }
    }
}
