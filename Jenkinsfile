stage('Deploy') {
    steps {
        sh """
        echo "🚀 Deploying..."

        cd ${WORKSPACE}/docker_deploy

        git pull origin main

        # Use Docker Compose V2 (correct way)
        docker compose version || true

        docker compose up -d --build
        """
    }
}
