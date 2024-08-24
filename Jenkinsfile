pipeline { 
    agent any 

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' my-eks22', contextName: '', credentialsId: 'kube-token', namespace: 'webapps', serverUrl: 'https://127E9436BA00F4179627C6652364C965.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' my-eks22', contextName: '', credentialsId: 'kube-token', namespace: 'webapps', serverUrl: 'https://127E9436BA00F4179627C6652364C965.gr7.us-east-1.eks.amazonaws.com']]) {
                 sh "kubectl get all -n webapps"
                }
            }
        }
    }
}

