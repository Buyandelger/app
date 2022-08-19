pipeline{
    agent { 
        dockerfile{
            filename 'Dockerfile' 
            label "buyandelger/getting-started.${env.BUILD_ID}"
            registryUrl 'https://registry.hub.docker.com'
            registryCredentialsId 'dockerHub'
        }
    }
    stages{
        stage('Build stage'){
            steps{
                sh 'echo build starting ....'        
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