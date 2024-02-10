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
                    // docker.build('solash25/first-app-test')
                     sh 'docker build -t solash25/first-app-test-v2 .'
                }
            }
        }
    }
}
