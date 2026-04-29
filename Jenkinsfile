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

        stage('Deploy (Local Server)') {
            steps {
                sh """
                mkdir -p ${APP_DIR}

                if [ ! -d "${APP_DIR}/.git" ]; then
                    echo "🚀 First time deploy - cloning repo"
                    git clone ${REPO} ${APP_DIR}
                fi

                cd ${APP_DIR}

                git pull origin main

                docker compose up -d --build
                """
            }
        }
    }
}
