pipeline{
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            sh 'npm install'
        }

        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }

        stage('Deliver') {
            sh './jenkins/scripts/deliver.sh'
            input message: 'Finished checking the website? (Click Proceed to continue)'
            sh './jenkins/scripts/kill.sh'
        }
    }
}