pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                git url: 'https://github.com/Godfrey22152/URL-Shortener.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests using the Angular CLI
                sh 'npm run test'
            }
        }

        stage('Build') {
            steps {
                // Build the Angular app for production
                sh 'npm run build -- --prod'
            }
        }

        stage('Start Server') {
            steps {
                // Assuming you have a script to start the server, replace 'start-server.sh' with the actual script name
                // This step assumes that the script starts a server that serves the built Angular application
                sh './start-server.sh'
            }
        }
    }

    post {
        always {
            // Clean up any temporary files or artifacts after the build and deployment
            deleteDir()
        }

        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed. Please check the logs for more details.'
        }
    }
}
