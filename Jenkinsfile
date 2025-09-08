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
                    withCredentials([usernamePassword(credentialsId: '0e2906e9-720a-4856-9225-9a34ce20cc9b', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                        bat "echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin"
                        bat "docker push sukasukasayasuka/github-demo:latest"
                    }

            }
        }
    }
}