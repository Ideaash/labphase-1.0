pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main',
                    credentialsId: 'Access_Github_Jenkins',
                    url: 'https://github.com/Ideaash/labphase-1.0.git'
                }
            }
        }

                stage("Docker Build and Push") {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t solash25/firestapptest .'
                }
            }
        }
        
    }
}
