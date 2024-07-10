pipeline {
    agent any

    environment {
        registry = 'https://registry.hub.docker.com'
        dockerCredential = 'dockerhub'
    }

    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }

        stage('Build image') {
            steps {
                script {
                    def app = docker.build("kristijanjovcevski/kiii-jenkins")
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.withRegistry(registry, dockerCredential) {
                        app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                        app.push("${env.BRANCH_NAME}-latest")
                    }
                }
            }
        }
    }
}
