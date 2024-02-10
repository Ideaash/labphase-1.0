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
        
        stage('Build') {
            steps {
                script {
                    docker.build('solash25/first-app-test')
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                // Authentification Docker Hub
                withDockerRegistry([credentialsId: 'DOCKER_HUB_ACCESS_JENKINS', url: 'https://index.docker.io/v1/']) {
                    // Pousser l'image vers Docker Hub
                    script {
                        docker.image('solash25').push('latest')
                    }
                }
            }
        }
    }
}
}