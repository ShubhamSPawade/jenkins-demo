pipeline {
    agent any

    environment {
        IMAGE_NAME = "shubhampawde/code-e-pariksha"   // Docker Hub repo name (lowercase)
        IMAGE_TAG  = "2.0.0"                          // Version tag
    }

    stages {

        stage('Start') {
            steps {
                echo "🚀 Pipeline started"
            }
        }

        // stage('Checkout Code') {
        //     steps {
        //         git branch: 'main', url: 'https://github.com/ShubhamSPawade/jenkins-demo.git'
        //     }
        // }

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
                echo 'Hello version (NEW!) 11v Working stage'
            }
        }
    }
}
