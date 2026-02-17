stage('Deploy') {
    steps {
        sh '''
        # Find container running on port 3000
        CONTAINER_ID=$(docker ps -q --filter "publish=3000")

        # Stop container if exists
        if [ ! -z "$CONTAINER_ID" ]; then
            docker stop $CONTAINER_ID
            docker rm $CONTAINER_ID
        fi

        # Run new container
        docker run -d -p 3000:3000 --name pipeline-container pipeline-app
        '''
    }
}
