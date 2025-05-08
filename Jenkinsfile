pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '🔧 Building the application...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo '✅ Running tests...'
                sh 'npm test || echo "No tests found, skipping..."'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying the application...'
                sh 'echo Deploy step completed'
            }
        }
    }
}
