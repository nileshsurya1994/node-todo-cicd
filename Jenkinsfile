pipeline {
    agent any
    
    stages {
        stage("code") {
            steps {
                git url: "https://github.com/nileshsurya1994/node-todo-cicd.git", branch: "master"
                echo 'Code clone successful..'
            }
        }
        
        stage("build and test") {
            steps {
                sh "sudo docker docker rmi $(docker images -q)"
                sh "sudo docker build -t nodejsapp ."
                echo 'Build successful'
            }
        }
        
        stage("scan image") {
            steps {
                echo 'Image scanning completed....'
            }
        }
        
        stage("Existing container Remove") {
            steps {
                sh "sudo docker rm -f nodejsapp"
                echo 'Existing container removed'
            }
        }
        
        stage("deploy") {
            steps {
                sh "sudo docker run -d --name nodejsapp -p 3000:3000 nodejsapp"
                echo 'Deployment completed'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline successfully executed!'
        }
        failure {
            echo 'Pipeline failed :('
        }
    }
}
