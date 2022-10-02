pipeline {
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'docker build -t sra .'
                sh 'nginx --version'
            }
        }
    }
}
