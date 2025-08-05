pipeline {
    agent any

    stages {
        stage("My First") {
            steps {
                echo "hello my project"
            }
        }

        stage("Docker Image") {
            steps {
                bat '''
                    docker-compose down
                    docker-compose up -d
                '''
            }
        }

        stage("Deploy") {
            steps {
                bat 'docker ps'
            }
        }
    }
}
