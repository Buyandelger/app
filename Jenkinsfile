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
                        def remote = [:]
                        remote.name = 'test'
                        remote.host = '192.168.210.131'
                        remote.user = 'admin'
                        remote.password = '123456'
                        remote.allowAnyHosts = true
                        sshCommand remote: remote, command: "docker run -d -p 3000:3000 buyandelger/getting-started.${env.BUILD_ID}"
                        //sshCommand remote: remote, command: "docker version"                        
                    }
                }
                //sh 'DONE !'
                //sh "docker run -d -p 3000:3000 buyandelger/getting-started.${env.BUILD_ID}"
            }
        }
    }
}