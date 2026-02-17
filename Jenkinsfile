pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'SAI', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6669514C16CA6F2C5F369D309AF9EE7C.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'SAI', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6669514C16CA6F2C5F369D309AF9EE7C.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
