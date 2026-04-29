pipeline {
    agent any

    stages {

        stage('Deploy') {
            steps {
                sh '''
                set -e

                echo "🚀 Deploying..."

                # use Jenkins checked-out code directly
                cd $WORKSPACE

                ls -la

                docker version

                docker compose up -d --build
                '''
            }
        }
    }
}
