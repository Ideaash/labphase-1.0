pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'ideaash',
                    credentialsId: 'Github',
                    url: 'https://github.com/Ideaash/labphase-1.0.git'
                }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build('username-DockerHub/first-app-test')
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                // Authentification Docker Hub
                withDockerRegistry([credentialsId: 'votre-identifiant-credentials-dockerhub', url: 'https://index.docker.io/v1/']) {
                    // Pousser l'image vers Docker Hub
                    script {
                        docker.image('username-DockerHub').push('latest')
                    }
                }
            }
        }
    }
}
}