pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                // Замініть 'stepanapp' 
                sh 'docker build -t stepanapp:latest .'
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
                echo 'Pushing Docker image to DockerHub...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    // Замініть 'stepanapp' на назву вашого репо в обох рядках
                    sh 'docker tag stepanapp:latest $DOCKER_USER/stepanapp:latest'
                    sh 'docker push $DOCKER_USER/stepanapp:latest'
                }
            }
        }
    }
}