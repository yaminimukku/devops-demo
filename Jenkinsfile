pipeline {
    agent any

    environment {
        IMAGE_NAME = "yaminimukku/devops-demo"
        TAG = "latest"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Cloning GitHub repo..."
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh "docker build -t $IMAGE_NAME:$TAG ."
            }
        }

        stage('Push Docker Image') {
            steps {
                echo "Logging into DockerHub and pushing image..."

                withCredentials([usernamePassword(
                    credentialsId: 'docker-cred',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh """
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker push $IMAGE_NAME:$TAG
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline SUCCESS 🚀"
        }
        failure {
            echo "Pipeline FAILED ❌"
        }
    }
}