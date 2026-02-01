pipeline {
    agent any

    environment {
        IMAGE_NAME = "shubhampawde/cep-test"   // Docker Hub repo name (lowercase)
        IMAGE_TAG  = "1.0.0"                          // Version tag
    }

    stages {

        stage('Start') {
            steps {
                echo "🚀 Pipeline started"
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'docker-branch', url: 'https://github.com/ShubhamSPawade/jenkins-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "🔨 Building Docker image..."
                    def customImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                    env.IMAGE_ID = customImage.id
                    echo "Image built with ID: ${env.IMAGE_ID}"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    echo "📦 Pushing Docker image to Docker Hub..."
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        docker.image("${IMAGE_NAME}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo "✅ Docker image successfully built and pushed: ${IMAGE_NAME}:${IMAGE_TAG}"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}
