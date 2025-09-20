pipeline {
    agent any
    stages {
        stage('Deploy WordPress') {
            steps {
                // Apply Kubernetes manifests
                sh '/opt/homebrew/bin/kubectl apply -f k8s/wordpress-deployment.yaml'
                sh '/opt/homebrew/bin/kubectl apply -f k8s/mysql-deployment.yaml'
                sh '/opt/homebrew/bin/kubectl apply -f k8s/wordpress-service.yaml'
            }
        }
        stage('Verify Deployment') {
            steps {
                sh '/opt/homebrew/bin/kubectl get pods -l app=wordpress'
                sh '/opt/homebrew/bin/kubectl get svc wordpress-service'
            }
        }
    }
}
