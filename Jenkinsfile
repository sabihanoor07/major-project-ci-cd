pipeline {
    agent any

    environment {
        APP_SERVER = "13.203.213.201"
        IMAGE_NAME = "devops-major-project"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Deploy to App Server') {
            steps {
                sshagent(['app-server-ssh']) {
                    sh """
                    ssh ubuntu@$APP_SERVER '
                      docker rm -f devops-app || true
                      docker run -d -p 8080:80 --name devops-app $IMAGE_NAME:latest
                    '
                    """
                }
            }
        }
    }
}
