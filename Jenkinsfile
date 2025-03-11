pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url:'https://github.com/Juhi5863/ci-cd.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t juhichoudhary/flask-ci-cd:latest .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-creds3', url: '']) {
                    sh 'docker push juhichoudhary/flask-ci-cd:latest'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f jc13-deployment.yaml'
            }
        }
    }
}


