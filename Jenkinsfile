pipeline {
    agent any
    
    stages {
        
        stage("code"){
            steps{
                git url: "https://github.com/nileshsurya1994/node-todo-cicd.git", branch: "master"
                echo 'bhaiyya code clone ho gaya...'
            }
        }
        stage("build and test"){
            steps{
                sh "sudo docker build -t nodejsapp ."
                echo 'code build bhi ho gaya'
            }
        }
        stage("scan image"){
            steps{
                echo 'image scanning ho gayi'
            }
        }
        stage("Existing container Remove")
             steps{
             sh "sudo docker rm -f nodejsapp"
             echo 'Existing conatiner is removed'
             }
        stage("deploy"){
            steps{
                sh "sudo docker run -d --name nodejsapp -p 3000:3000 nodejsapp"
                echo 'deployment ho gayi'
            }
        }
    }
}

