pipeline {
    agent any
    environment {
        REGISTRY = "docker.io/jhadeepakkumar14"
        IMAGE = "wordpress-k8s"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/jhas3c/wordpress-k8s-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $REGISTRY/$IMAGE:$BUILD_NUMBER .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
                    sh 'docker push $REGISTRY/$IMAGE:$BUILD_NUMBER'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
