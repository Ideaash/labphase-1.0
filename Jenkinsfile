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
                script {
                    echo "bonjou"
                }
            }
        }
    }
}
