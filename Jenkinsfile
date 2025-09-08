pipeline {
    agent any

    stages {
        stage('Verify') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sukasukasayasuka/github-demo .'
            }
        }

        stage('Push Docker Image') {
            steps {
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                        sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
                        sh "docker push sukasukasayasuka/github-demo:latest"
                    }

            }
        }
    }
}