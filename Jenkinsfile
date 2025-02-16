pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/harini1810/flask.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t flask-app:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker run -d -p 5000:5000 --name flask-container flask-app:latest'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    bat 'docker stop flask-container'
                    bat 'docker rm flask-container'
                }
            }
        }
    }
}
