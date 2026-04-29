pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'echo "No tests yet"'
            }
        }

        stage('Deploy (Local Server)') {
            steps {
                sh '''
                echo "🚀 Deploying from Jenkins workspace..."

                ls -la

                docker compose up -d --build || docker-compose up -d --build
                '''
            }
        }
    }
}
