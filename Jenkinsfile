pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k9-token', namespace: 'webapps', serverUrl: 'https://883239B3CE26BB0977F3CD7DE8AF365A.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k9-token', namespace: 'webapps', serverUrl: 'https://883239B3CE26BB0977F3CD7DE8AF365A.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
