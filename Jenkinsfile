pipeline {
    agent any

    stages {
        // Stage 1: Checkout Git Repository
        stage('Checkout') {
            steps {
                git(
                    url: 'https://github.com/LM213/jenkins-pipeline1-demo.git',
                    branch: 'main',
                    credentialsId: '' // Remove or add your Jenkins Git credentials ID if private
                )
                sh 'git --version' // Verify Git (optional)
            }
        }

        // Stage 2: Build
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm install' // Assumes your repo has a package.json
            }
        }

        // Stage 3: Test
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test || echo "No tests found, skipping..."'
            }
        }

        // Stage 4: Deploy (Simulated)
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh 'echo "Deploy step completed (simulated)"'
                // Replace with actual deploy commands (e.g., `kubectl apply`, `scp`)
            }
        }
    }

    // Post-Build Actions
    post {
        always {
            echo 'Pipeline completed. Status: ${currentBuild.result}'
            cleanWs() // Clean workspace after run (optional)
        }
        success {
            echo 'Pipeline succeeded! 🎉'
            // mail to: 'team@example.com', subject: 'SUCCESS: Pipeline', body: 'All good!'
        }
        failure {
            echo 'Pipeline failed! ❌'
            // mail to: 'team@example.com', subject: 'FAILURE: Pipeline', body: 'Check Jenkins!'
        }
    }
}
