pipeline {
    agent any

    environment {
        CI_ENVIRONMENT = 'develop'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/fairulmuhammadcodeigniter4.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh 'composer install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'vendor/bin/phpunit'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying CodeIgniter 4...'
                sh 'cp -r * /var/www/html/'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline executed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
