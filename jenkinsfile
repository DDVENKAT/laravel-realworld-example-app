pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'composer install'
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'vendor/bin/phpunit'
            }
        }
        
        stage('Build and Deploy') {
            steps {
                sh 'php artisan config:cache'
                sh 'php artisan route:cache'
                sh 'php artisan migrate --force'
                sh 'php artisan optimize --force'
            }
        }
    }
}
