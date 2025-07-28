pipeline{
    agent any
    stages{
        stage(" first step"){
            steps{
                echo "hello my project"
            }
        }
        
        stage("second "){
            steps{
                git url:"https://github.com/sandepsarma/repotwo.git" , branch:"main"
            }
        }
        
        stage("thirrd"){
            steps{
                bat 'docker build -t myimg .'
            }
        }
        
        stage("deploy"){
            steps{
                bat 'docker run -p 80:80 -d myimg'
            }
        }
    }
}
