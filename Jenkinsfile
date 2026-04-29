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

                echo "📂 Files in project:"
                ls -la

                docker version

                # only works if docker-compose.yml exists
                docker-compose up -d --build
                """
            }
        }
    }
}
