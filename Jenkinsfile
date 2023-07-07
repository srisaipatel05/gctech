pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def appImage = docker.build("srisaipatel/gctech:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'bunny') {
                        def appImage = docker.image("srisaipatel/gctech:${env.BUILD_NUMBER}")
                        appImage.push()
                    }
                }
            }
        }
    }
}
