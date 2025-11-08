pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: 'EKS-1', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://814CDBD80EACA4C08BD4D3C1673E2D58.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: 'EKS-1', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://814CDBD80EACA4C08BD4D3C1673E2D58.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
