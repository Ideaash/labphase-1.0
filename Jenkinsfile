pipeline {
    agent any

    stages {
        stage('Setup Docker Permissions') {
            steps {
                script {
                    // Add Jenkins user to Docker group
                    sh 'sudo usermod -aG docker jenkins'

                    // Set Docker socket permissions for Jenkins user
                    sh 'sudo chown jenkins:docker /var/run/docker.sock'
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

        stage('Docker Build and Push') {
            steps {
                script {
                    // Build and push Docker image
                    docker.build('solash25/firestapptest').push()
                }
            }
        }
    }
}
