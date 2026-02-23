pipeline {
    agent any

    environment {
        IMAGE_NAME = "anjana1234okok/myapp"
        TAG = "v1"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/AnjanaMangamthara/real-pipeline-fresh.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$TAG .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                usernameVariable: 'DOCKER_USER',
                passwordVariable: 'DOCKER_PASS')]) {

                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    '''
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE_NAME:$TAG'
            }
        }

    }
}
