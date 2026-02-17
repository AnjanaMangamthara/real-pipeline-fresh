pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/AnjanaMangamthara/real-pipeline-fresh.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t pipeline-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop pipeline-container || true'
                sh 'docker rm pipeline-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name pipeline-container pipeline-app'
            }
        }

    }
}
