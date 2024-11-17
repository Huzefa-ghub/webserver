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
                sh '''
                    npm install
                    npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: Run tests (adjust based on your test framework)
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the website...'
                // Copy built website files to the deployment directory
                sh '''
                    sudo rm -rf $DEPLOY_DIR/*
                    sudo cp -r dist/* $DEPLOY_DIR/
                '''
                echo 'Deployment completed successfully.'
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
