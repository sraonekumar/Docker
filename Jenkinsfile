pipeline {
    agent { docker 'nginx:latest' } 
    stages {
        stage('Example Build') {
            steps {
                sh 'trivy image nginx:latest'
            }
        }
    }
}
