pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://B2B45A9E578F7A5DEABFE310E400C05D.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f svc-acc.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://B2B45A9E578F7A5DEABFE310E400C05D.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
