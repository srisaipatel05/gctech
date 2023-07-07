pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def appImage = docker.build("your-dockerhub-srisaipatel/gctech:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'bunny') {
                        def appImage = docker.image("your-dockerhub-srisai/gctech:${env.BUILD_NUMBER}")
                        appImage.push()
                    }
                }
            }
        }
    }
}
