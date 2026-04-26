pipeline {
    agent any

    environment {
        IMAGE_NAME = "yaminimukku123/devops-demo"
        TAG = "latest"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning GitHub repo...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t $IMAGE_NAME:$TAG ."
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Logging into DockerHub and pushing image...'

                withCredentials([usernamePassword(
                    credentialsId: 'docker-cred',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker push $IMAGE_NAME:$TAG
                    '''
                }
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running container...'
                sh "docker run -d -p 8081:80 --name test-container $IMAGE_NAME:$TAG || true"
            }
        }

        stage('Test Application') {
            steps {
                echo 'Testing application...'
                sh "curl http://localhost:8081"
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Cleaning up container...'
                sh "docker stop test-container || true"
                sh "docker rm test-container || true"
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS '
        }
        failure {
            echo 'Pipeline FAILED❌'
        }
    }
}