pipeline{
    agent any
    stages{
        stage('Build stage'){
            sh 'echo build starting ....'        
            steps{
                agent { 
                    dockerfile{
                        image "buyandelger/getting-started.${env.BUILD_ID}"
                        registryUrl 'https://registry.hub.docker.com'
                        registryCredentialsId 'dockerHub'
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