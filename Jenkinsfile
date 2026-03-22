pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E5B93F04A14BA55E08A8749806EFA559.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E5B93F04A14BA55E08A8749806EFA559.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
