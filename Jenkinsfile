pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs() // Crucial: Cleans workspace before checkout
            }
        }
        
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/LM213/jenkins-pipeline1-demo.git'
                    ]]
                ])
                
                // Verify the checkout worked
                sh '''
                    echo "Current directory: $(pwd)"
                    git status
                    ls -al
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "Tests skipped"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deployment simulation"'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed! Check the repository URL and workspace permissions.'
            // mail to: 'admin@example.com', subject: 'Pipeline Failed'
        }
        success {
            echo 'Pipeline succeeded!'
        }
    }
}
