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
                sh '''
                set -e

                echo "🚀 Deploying..."

                # Clone if not exists
                if [ ! -d "${WORKSPACE}/docker_deploy/.git" ]; then
                    git clone ${REPO} ${WORKSPACE}/docker_deploy
                fi

                cd ${WORKSPACE}/docker_deploy

                git pull origin main || true

                docker version

                # 🔥 FIX: force correct compose execution
                /usr/bin/docker compose up -d --build
                '''
            }
        }
    }
}
