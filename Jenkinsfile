pipeline{
    agent { dockerfile true }
    stages{
        stage('Build stage'){
            steps{
                sh 'echo build starting ....'
                script {
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
                            def customImage = docker.build("buyandelger/getting-started.${env.BUILD_ID}")
                            customImage.push()
                        }
                }
            }
        }
        stage('Deploy to test server ....'){
            steps{
                sh 'ssh admin@192.168.210.131'
                sh "docker run -d -p 3000:3000 buyandelger/getting-started.${env.BUILD_ID}"
            }
        }
    }
}