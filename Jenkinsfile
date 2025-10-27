pipeline {
    agent any
    
    environment {
        IMAGE_NAME = "myapp"
        CONTAINER_NAME = "myapp-con"
        PORTS = "-p 3000:3000"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container...'
                sh "docker run -d --name ${CONTAINER_NAME} ${PORTS} ${IMAGE_NAME}"
            }
        }
    }

    post {
        success {
            echo '✅ Build and container run successful!'
        }
        failure {
            echo '❌ Build failed.'
        }
    }
}
