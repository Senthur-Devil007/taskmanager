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
                    url: 'https://github.com/Senthur-Devil007/taskmanager.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t task-manager:v1 .'
            }
        }

        stage('Docker Images') {
            steps {
                bat 'docker images'
            }
        }

    }

    post {

        success {
            echo '======================================='
            echo 'Task Manager Build Successful'
            echo '======================================='
        }

        failure {
            echo '======================================='
            echo 'Task Manager Build Failed'
            echo '======================================='
        }

    }

}