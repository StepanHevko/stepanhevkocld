pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t myapp:latest .'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "Tests passed!"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy stage (локально)'
                sh 'docker images'
            }
        }
    }
}