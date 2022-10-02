pipeline {
    agent any
    stages {
         stage('Build') {
             steps {
                 sh 'docker build -t sraonekumar/Docker:latest .'
             }
        }
        stage('Example Build') {
            steps {
                sh 'trivy image sraonekumar/Docker:latest'
            }
        }
    }
}
