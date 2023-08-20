pipeline {
    agent none
    stages {
        stage('Deploy') {
            agent any
            steps {
                withAWS(region: 'us-east-1', credentials: 'aws-credential') {
                    sh "aws eks update-kubeconfig --name sd2660-devops-eks"
                    // sh "kubectl config set-context --current --namespace eks-ns"
                    sh "kubectl apply -f mongodb.yaml"
                    sh "kubectl apply -f backend.yaml"
                    sh "kubectl apply -f frontend.yaml"
                    sh "kubectl apply -f ingress.yml"
                }
            }
        }
    }
}