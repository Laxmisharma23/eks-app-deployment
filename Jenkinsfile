pipeline {
agent any 
  stages {
    stage('Deploy eks app') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
        }
    }
  }

}
