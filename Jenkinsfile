pipeline {
    agent {
        docker { image 'node:12-alpine'}
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo build stage'
                sh 'node --version'
            }
        }
        stage('Test') {
            steps {
                sh 'echo test stage'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo deploy stage'
            }
        }
    }
}