pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Pulling latest code from GitHub...'
                git branch: 'main',
                url: 'https://github.com/Satish-kl/Jenkins-Car-website.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Car Website...'
                sh '''
                echo "Static website build completed successfully"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to Apache web server...'
                sh '''
                sudo rm -rf ${DEPLOY_DIR}/*
                sudo cp -r * ${DEPLOY_DIR}/
                '''
            }
        }
    }

    post {
        success {
            echo 'Car Website deployed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check the build logs.'
        }
    }
}