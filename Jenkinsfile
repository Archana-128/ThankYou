pipeline {
    agent any
    stages {

        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build --no-cache -t ThankYou-image .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker rm -f ThankYou-container || exit 0
                docker run -d -p 8083:80 --name ThankYou-container ThankYou-image
                '''
            }
        }
    }
}
