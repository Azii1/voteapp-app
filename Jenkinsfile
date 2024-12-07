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
        
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'azii1', passwordVariable: 'Cloud1234')]) {
                    sh 'echo "$Cloud1234" | docker login -u "$azii1" --password-stdin'
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
