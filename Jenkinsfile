pipeline {
    agent any

    environment {
        SERVER = "192.168.7.239"
        APP_DIR = "/var/www/docker_deploy"
        REPO = "https://github.com/montasir-eee/docker_deploy.git"
    }

    stages {

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'echo "No tests yet"'
            }
        }

        stage('Deploy (Bootstrap + Update)') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'prod-server-key', keyFileVariable: 'KEY')]) {
                    sh """
                    ssh -i $KEY -o StrictHostKeyChecking=no root@${SERVER} '
                    
                    # Create folder if not exists
                    mkdir -p ${APP_DIR}

                    # First time deploy OR update
                    if [ ! -d "${APP_DIR}/.git" ]; then
                        echo "🚀 First time deploy - cloning repo"
                        git clone ${REPO} ${APP_DIR}
                    fi

                    cd ${APP_DIR}

                    git pull origin main

                    docker-compose up -d --build

                    '
                    """
                }
            }
        }
    }
}
