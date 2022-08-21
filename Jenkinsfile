/*pipeline{
    agent any
    stages{
        stage('Build stage'){            
            steps{
                sh 'echo build starting ....'        
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
}*/

node {
    checkout scm
    docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
        def customImage = docker.build("buyandelger/getting-started:${env.BUILD_ID}")
        customImage.push()
    }

    docker.withServer('ssh://192.168.210.131','centoscred'){
        docker.image("buyandelger/getting-started:${env.BUILD_ID}").withRun('-p -d 3000:3000')
    }
}