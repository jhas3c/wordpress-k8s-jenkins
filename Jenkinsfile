pipeline {
    agent any
    stages {
        stage('Deploy WordPress') {
            steps {
                // Apply Kubernetes manifests
                sh 'kubectl apply -f k8s/wordpress-deployment.yaml'
                sh 'kubectl apply -f k8s/wordpress-service.yaml'
            }
        }
        stage('Verify Deployment') {
            steps {
                sh 'kubectl get pods -l app=wordpress'
                sh 'kubectl get svc wordpress-service'
            }
        }
    }
}
