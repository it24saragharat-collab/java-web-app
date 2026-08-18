pipeline {
    agent any

    tools {
        jdk 'JDK25'
        maven 'Maven-3.9.16'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/it24saragharat-collab/java-web-app.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    if exist deployed rmdir /S /Q deployed
                    mkdir deployed
                    copy target\\java-web-app-1.0.0.jar deployed\\
                    echo Application deployed successfully!
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed.'
        }
    }
}