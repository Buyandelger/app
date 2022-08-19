/*node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {

        def customImage = docker.build("buyandelger/getting-started.${env.BUILD_ID}")

        /* Push the container to the custom Registry */
  /*      customImage.push()
    }
}*/

pipeline{
    agent { dockerfile true }
    stages{
        stage('test'){
            steps{
                sh 'echo just for testing'
            }
        }
    }
}