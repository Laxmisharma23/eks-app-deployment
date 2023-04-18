pipeline {
  agent any
  stages {
    stage('Deploying node.js container to Kubernetes') {
      steps {
        script {
          sh "aws eks --region us-east-1 update-kubeconfig --name laxmi-EKS-Cluster"
            sh "kubectl apply -f deployment.yaml"
              sh "kubectl apply -f service.yaml"
        }
      }
    }
  }
}
