pipeline {
    agent any

    environment {
        // Optional: Docker Hub credentials and image name.
        // Uncomment and configure if you plan to push the image.
        // DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials-id')
        // IMAGE_NAME = "your-dockerhub-username/minimal-flask-app"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as "minimal-flask-app:latest"
                    sh "docker build -t minimal-flask-app:latest ."
                }
            }
        }

        // Uncomment the stage below if you want to push the image to Docker Hub.
        /*
        stage('Push Docker Image') {
            steps {
                script {
                    sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                    sh "docker push ${IMAGE_NAME}:latest"
                }
            }
        }
        */
    }

    post {
        always {
            // Optionally, clean up any resources or send notifications.
            echo "Pipeline finished."
        }
    }
}
