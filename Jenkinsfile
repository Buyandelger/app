pipeline{
    agent { 
        dockerfile{
            filename 'Dockerfile' 
            registryUrl 'https://registry.hub.docker.com'
            registryCredentialsId 'dockerHub'
            additionalBuildArgs "buyandelger/getting-started.${env.BUILD_ID}"
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