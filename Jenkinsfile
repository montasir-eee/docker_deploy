stage('Deploy') {
    steps {
        sh """
        echo "🚀 Deploying from Jenkins workspace..."

        cd ${WORKSPACE}/docker_deploy

        git pull origin main

        # Use HOST docker engine
        docker version

        # IMPORTANT: use compose v2 syntax
        docker compose up -d --build
        """
    }
}
