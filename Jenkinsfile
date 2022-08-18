pipeline {
    agent { dockerfile true }
    stages {
        stage('Build') {
            steps {
                sh 'echo ======== build stage started ========'
                sh 'docker build -t getting-started'
                sh 'echo ======== build stage ended ========='
            }
        }
        stage('Run'){
            steps {
                sh 'echo run stage started'
                sh 'docker run -dp 3000:3000 getting-started'
            }    
        }
    }
}