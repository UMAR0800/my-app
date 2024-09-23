pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the code from the GitHub repository
                git 'https://github.com/UMAR0800/simple-python.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t python-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the container and capture the output
                    sh 'docker run --name python-app-container python-app'
                }
            }
        }

        stage('Clean Up') {
            steps {
                script {
                    // Stop and remove the container
                    sh 'docker stop python-app-container || true'
                    sh 'docker rm python-app-container || true'
                    
                    // Remove the image
                    sh 'docker rmi -f python-app'
                }
            }
        }
    }

    post {
        always {
            // Clean up any leftover containers
            sh 'docker system prune -f'
        }
    }
}
