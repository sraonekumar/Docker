pipeline {
  environment {
    imagename = "msravankumar/srav_private_docker_hub"
    registryCredential = 'doc-hub'
    dockerImage = ''
  }
  agent any
  stages {
      
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build nginx
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"
 
      }
    }
  }
}
