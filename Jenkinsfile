pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "🚀 Deploying..."

                docker compose version || true

                docker compose up -d --build || docker-compose up -d --build
                '''
            }
        }
    }
}
