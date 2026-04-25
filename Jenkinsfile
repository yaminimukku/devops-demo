pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo "Checking out code..."
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t devops-demo:latest .'
            }
        }
        stage('Push Docker Image') {
           steps {
                 echo "Pushing image to DockerHub..."
                 sh 'docker tag devops-demo:latest yourdockerhub/devops-demo:latest'
                 sh 'docker push yourdockerhub/devops-demo:latest'
                }
           }
    }
}