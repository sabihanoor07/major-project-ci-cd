pipeline {
    agent any

    environment {
        APP_SERVER = "13.203.213.201"
        IMAGE_NAME = "devops-major-project"
        REPO_URL   = "https://github.com/sabihanoor07/major-project-ci-cd.git"
        APP_DIR    = "major-project-ci-cd"
    }

    stages {

        stage('Build Docker Image (Jenkins)') {
            steps {
                echo "Building Docker image on Jenkins server"
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Deploy to App Server') {
            steps {
                sshagent(['app-server-ssh']) {
                    sh """
                    ssh -o StrictHostKeyChecking=no ubuntu@${APP_SERVER} '
                        set -e
                        if [ ! -d ${APP_DIR} ]; then
                            git clone ${REPO_URL}
                        fi
                        cd ${APP_DIR}
                        git pull origin main
                        docker rm -f devops-app || true
                        docker build -t ${IMAGE_NAME}:latest .
                        docker run -d -p 8080:80 --name devops-app ${IMAGE_NAME}:latest
                    '
                    """
                }
            }
        }
    }
}

