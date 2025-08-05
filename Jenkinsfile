pipeline {
    agent any

    stages {
        stage("My First") {
            steps {
                echo "hello my project"
            }
        }

        /*
        stage("Git Cloning") {
            steps {
                git url: 'https://github.com/sandepsarma/repotwo.git', branch: 'main'
            }
        }
        */

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
