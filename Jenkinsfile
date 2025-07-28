pipeline {
    agent any

    environment {
        IMAGE_NAME = "myimg"
        CONTAINER_NAME = "mycontainer"
        HOST_PORT = "8080"
        CONTAINER_PORT = "80"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/sandepsarma/repotwo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Cleanup Old Container') {
            steps {
                script {
                    // Stop and remove existing container if running
                    bat """
                    docker ps -q --filter "name=%CONTAINER_NAME%" | for /F "tokens=*" %%i in ('more') do docker stop %%i && docker rm %%i
                    """
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                bat "docker run -d --name %CONTAINER_NAME% -p %HOST_PORT%:%CONTAINER_PORT% %IMAGE_NAME%"
            }
        }
    }

    post {
        failure {
            echo "Build failed. Check logs above."
        }
        success {
            echo "App deployed successfully on http://localhost:%HOST_PORT%"
        }
    }
}

