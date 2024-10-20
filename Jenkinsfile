@Library("Shared") _
pipeline {
    agent { label 'vinod' }

    stages {
        
        stage('Code') {
            steps {
                script{
                clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
               docker_build("notes-app","latest","siddhant1130")
            }
           }
        }
        stage('Push to DockerHub') {
            steps {
               script{
                   docker_push("notes-app","latest","siddhant1130")
               }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is Deploying the code'
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
