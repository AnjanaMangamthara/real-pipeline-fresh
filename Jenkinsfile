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
                echo "Testing Jenkins at"
                sh 'docker build -t pipeline-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                CONTAINER_ID=$(docker ps -q --filter "publish=3000")

                if [ ! -z "$CONTAINER_ID" ]; then
                    docker stop $CONTAINER_ID
                    docker rm $CONTAINER_ID
                fi

                docker run -d -p 3000:3000 --name pipeline-containernew1 pipeline-app
                '''
            }
        }

    }
}
