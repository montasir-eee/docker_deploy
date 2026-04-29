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
                set -e

                echo "🚀 Deploying from Jenkins workspace..."

                docker-compose up -d --build
                '''
            }
        }
    }
}
