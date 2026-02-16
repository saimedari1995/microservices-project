pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MSK', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BD68EAD1ED9122A6D195299D7C927A4F.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MSK', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BD68EAD1ED9122A6D195299D7C927A4F.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
