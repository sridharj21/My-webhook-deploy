pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sridharj21/My-webhook-deploy.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-web-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop python-web-app || true
                docker rm python-web-app || true
                docker run -d --name python-web-app -p 6000:5000 python-web-app
                '''
            }
        }
    }
}
