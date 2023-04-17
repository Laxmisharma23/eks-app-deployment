pipeline {
  agent any
  stages {
    stage('Deploying node.js container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
        }
      }
    }
  }
}
