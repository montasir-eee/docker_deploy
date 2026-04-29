pipeline {
    agent any

    environment {
        APP_DIR = "${WORKSPACE}/docker_deploy"
        REPO = "https://github.com/montasir-eee/docker_deploy.git"
    }

    stages {

        stage('Deploy') {
            steps {
                sh '''
                set -e

                echo "🚀 Deploying..."

                # clean old workspace (IMPORTANT)
                rm -rf ${APP_DIR}

                # fresh clone
                git clone ${REPO} ${APP_DIR}

                cd ${APP_DIR}

                docker version

                docker compose up -d --build
                '''
            }
        }
    }
}
