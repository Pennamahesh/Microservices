pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'calico-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2BD193650EFBE0FDC5EA578AFAF0286F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'calico-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://2BD193650EFBE0FDC5EA578AFAF0286F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
