pipeline {
    agent any

    environment {
        IMAGE_NAME = "php-jenkins-app"
        CONTAINER_NAME = "php-app-container"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/anggitamikom/php-jenkins-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                echo "Installing dependencies..."
                '''
            }
        }

        stage('Run Unit Test') {
            steps {
                sh '''
                echo "Running unit test..."
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Deploy Docker Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true

                docker run -d \
                --name $CONTAINER_NAME \
                -p 8081:80 \
                $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline Berhasil!'
        }

        failure {
            echo 'Pipeline Gagal!'
        }
    }
}