pipeline {
    agent {
        docker {
            // Use a Node.js with Angular CLI Docker image
            image 'node:14'
            args '-p 4200:4200' // Expose port 4200 for serving the application
        }
    }

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
                // Serve the built Angular application using the Angular CLI
                sh 'npm run start'
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
