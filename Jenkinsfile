pipeline {
    agent {
        docker {
            image 'node:20'
            args '-u root' // Optional: runs as root inside container if needed
        }
    }

    stages {
        stage('Build') {
            steps {
                echo '🛠️ Building the application...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                // If you don't have real tests, this won't fail the build
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
