pipeline {
    agent any
    stages {
         stage('Build') {
             steps {
                 sh 'docker build -t sraonekumar/docker:latest .'
             }
        }
        stage('Example Build') {
            steps {
                sh 'trivy image sraonekumar/docker:latest'
            }
        }
    }
}
