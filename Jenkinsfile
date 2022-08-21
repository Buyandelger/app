pipeline{
    agent any
    stages{
        stage('Build stage'){            
            steps{
                sh 'echo build starting ....'        
                script{
                    node{
                        checkout scm
                        docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
                            def customImage = docker.build("buyandelger/getting-started.${env.BUILD_ID}")
                            customImage.push()
                        }
                    }
                }                          
            }
        }
        stage('Deploy to test server ....'){
            steps{
                script{
                    node{
                        checkout scm
                        docker.withServer('ssh://192.168.210.131','centoscred'){
                            docker.image("buyandelger/getting-started.${env.BUILD_ID}").withRun('-d -p 3000:3000'){
                                sh 'ready to use'
                            }                                 
                        }
                    }
                }
                //sh "docker run -d -p 3000:3000 buyandelger/getting-started.${env.BUILD_ID}"
            }
        }
    }
}