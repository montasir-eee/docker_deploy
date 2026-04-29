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
                set -e

                echo "🚀 Deploying..."

                if [ ! -d "${APP_DIR}/.git" ]; then
                    git clone ${REPO} ${APP_DIR}
                fi

                cd ${APP_DIR}
                git pull origin main

                docker version
                docker-compose up -d --build
                """
            }
        }
    }
}
