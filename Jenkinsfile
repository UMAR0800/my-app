pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the code from the GitHub repository
                git 'https://github.com/UMAR0800/simple-python-app.git'
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
                    sh 'docker run python-app'
                }
            }
        }

        stage('Clean Up') {
            steps {
                script {
                    // Optionally clean up Docker containers and images
                    sh 'docker rmi python-app'
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
