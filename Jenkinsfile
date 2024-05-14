pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'graphql-node-app'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'TWOJ_ADRES_DO_REPO', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${env.DOCKER_IMAGE}:latest").run("-p 4000:4000")
                }
            }
        }
    }
}
