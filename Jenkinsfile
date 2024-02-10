pipeline {
    agent any

    stages {
        stage('Setup Docker Permissions') {
            steps {
                script {
                    // Configure Docker permissions
                    sh 'sudo usermod -aG docker jenkins || true' // Add Jenkins to Docker group
                    sh 'sudo chown jenkins:docker /var/run/docker.sock || true' // Set ownership of Docker socket
                }
            }
        }

        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from Git repository
                    git branch: 'main', credentialsId: 'Access_Github_Jenkins', url: 'https://github.com/Ideaash/labphase-1.0.git'
                }
            }
        }

        stage('Build the Docker image') {
            steps {
                script {
                    // Build Docker image  docker.build('solash25/first-app-test')
                    sh 'docker build -t solash25/first-app-test-v2 .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                // Authenticate with Docker Hub
                withDockerRegistry([credentialsId: 'DOCKER_HUB_ACCESS_JENKINS', url: 'https://index.docker.io/v1/']) {
                    // Push the image to Docker Hub
                    script {
                        docker.image('solash25/first-app-test-v2').push('latest')
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Deploy image to Kind cluster
                    sh 'kind create cluster --name cluster-devops'
                    sh 'kubectl apply -f deployment.yaml'
                    sh 'kubectl apply -f service.yaml'
                }
            }
        }
    }
}
