pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'azii1/voteapp-app'
        DOCKER_TAG = 'latest' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Azii1/voteapp-app.git',
                    credentialsId: 'github-credentials-id'
            }
        }
    }
}

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${azii1/voteapp-app}:${latest} .'
            }
        }

        stage('Tag Docker Image') {
            steps {
                echo 'Tagging Docker image...'
                sh 'docker tag ${azii1/voteapp-app}:${latest} ${azii1/voteapp-app}:${latest}'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                echo 'Logging into Docker Hub...'
                sh '''
                echo "${Cloud1234}" | docker login -u "${azii1}" --password-stdin
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Pushing Docker image to Docker Hub...'
                sh 'docker push ${azii1/voteapp-app}:${latest}'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'docker logout'
        }
        success {
            echo 'Docker image successfully pushed to Docker Hub!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
