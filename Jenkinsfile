pipeline {
    agent any
    
    environment {
        // Define the Docker image name here for reuse
        IMAGE_NAME = 'mudragallasrilakshmi/nodeapp'
    }

    stages {
        stage('Checkout Source') {
            steps {
                // Properly checkout your Git repository
                git branch: 'main', credentialsId: 'git-hub', url: 'https://github.com/srilakshmi2224/node.js.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Building the Docker image with the Docker Pipeline plugin syntax
                    docker.build("${env.IMAGE_NAME}:latest")
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    // Login and push the Docker image to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                        docker.image("${env.IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
