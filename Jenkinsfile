pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo build stage'
                sh 'docker build -t getting-started'
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