pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main',
                    url: 'https://github.com/Azii1/voteapp-app.git',
                    credentialsId: 'Github-credentials'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-app-image .'
            }
        }

        stage('Tag Docker Image') {
            steps {
                echo 'Tagging Docker image...'
                sh 'docker tag my-app-image azii1/voteapp-app:latest'
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Pushing Docker image...'
                sh 'docker push azii1/voteapp-app:latest'
            }
        }
    }
}
