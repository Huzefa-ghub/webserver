pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html" // Directory where the website will be hosted
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the source code...'
                checkout scm // Pulls the source code from the Git repository
            }
        }

        stage('Build') {
            steps {
                echo 'Building the website...'
                // Example: Install dependencies and build the site
                // Modify commands according to your project
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: Run tests (adjust based on your test framework)
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the website...'
                // Copy built website files to the deployment directory
                     sshagent (credentials: ['deploy_user']) {
                     sh 'ssh -o StrictHostKeyChecking=no workspace/target/* ec2-user@ec2-15-207-249-165:/var/www/html'
                     }
                 }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
