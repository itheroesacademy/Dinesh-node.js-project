pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    sh 'docker build -t node-docker-app .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    echo 'Running Docker container...'
                    sh 'docker run -d -p 1011:1011 --name node-docker-app-container node-docker-app'
                }
            }
        }
        stage('Test Application') {
            steps {
                script {
                    echo 'Running tests...'
                    // You can add any test commands here, such as using curl to test endpoints
                    sh 'sleep 10' // Give the container some time to start
                    sh 'curl http://localhost:1011'
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'Cleaning up...'
               # sh 'docker stop node-docker-app-container || true'
               # sh 'docker rm node-docker-app-container || true'
               # sh 'docker rmi node-docker-app || true'
            }
        }
    }
}
