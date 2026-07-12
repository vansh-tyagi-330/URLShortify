pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo 'Code is available from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t urlshortify .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop urlshortify-container || true
                docker rm urlshortify-container || true
                docker run -d -p 3000:3000 --name urlshortify-container urlshortify
                '''
            }
        }
    }
}