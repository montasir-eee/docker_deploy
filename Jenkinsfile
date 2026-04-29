pipeline {
    agent any

    environment {
        APP_DIR = "${WORKSPACE}/docker_deploy"
        REPO = "https://github.com/montasir-eee/docker_deploy.git"
    }

    stages {

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'echo "No tests yet"'
            }
        }

        stage('Deploy') {
            steps {
                sh """
                echo "🚀 Deploying..."

                cd ${WORKSPACE}/docker_deploy || git clone ${REPO} ${WORKSPACE}/docker_deploy

                cd ${WORKSPACE}/docker_deploy

                git pull origin main || true

                docker version

                docker compose up -d --build
                """
            }
        }
    }
}
