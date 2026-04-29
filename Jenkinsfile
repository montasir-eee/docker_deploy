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
                sshagent(['prod-server-key']) {
                    sh """
                    ssh -o StrictHostKeyChecking=no root@${SERVER} '
                    
                    # 1. Create folder if not exists
                    mkdir -p ${APP_DIR}

                    # 2. If first time, clone repo
                    if [ ! -d "${APP_DIR}/.git" ]; then
                        echo "🚀 First time deploy - cloning repo"
                        git clone ${REPO} ${APP_DIR}
                    fi

                    # 3. Go to project
                    cd ${APP_DIR}

                    # 4. Pull latest code (for updates)
                    git pull origin main

                    # 5. Deploy with Docker
                    docker-compose up -d --build

                    '
                    """
                }
            }
        }
    }
}
