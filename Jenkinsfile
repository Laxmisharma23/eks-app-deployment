pipeline {

  environment {
    dockerimagename = "388328004932.dkr.ecr.us-east-1.amazonaws.com/laxmi-ecr-repo:latest"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/Laxmisharma23/eks-app-deployment.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }

    stage('Pushing Image') {
      environment {
               ECRCrediantial = 'aws-credentials'
           }
      steps{
        script {
          docker.AmazonElasticContainerRegistry( 'https://us-east-1.console.aws.amazon.com/', ECRCrediantial ) {
            dockerImage.push("latest")
          }
        }
      }
    }

    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
        }
      }
    }

  }

}
