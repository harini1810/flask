pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/harini1810/flask.git'
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
                    bat 'docker run -d -p 5000:5000 flask-app:latest'
                }
            }
        }

        stage('Cleanup') {
            steps {
                script {
                    bat 'docker stop $(docker ps -q --filter ancestor=flask-app:latest)'
                    bat 'docker rm $(docker ps -aq --filter ancestor=flask-app:latest)'
                }
            }
        }
    }
}
