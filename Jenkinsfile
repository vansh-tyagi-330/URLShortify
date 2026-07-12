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
                bat 'docker build -t urlshortify .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker stop urlshortify-container || exit /b 0
                docker rm urlshortify-container || exit /b 0
                docker run -d -p 3000:3000 --name urlshortify-container urlshortify
                '''
            }
        }
    }
}