pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('doc-hub')
    }
    
    stages {
         stage('Build') {
             steps {
                 sh 'docker build -t sraonekumar/docker:latest .'
             }
        }
        stage('Trivy Scan for Build') {
            steps {
                sh 'trivy image sraonekumar/docker:latest'
            }
        }
		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sraonekumar/docker:latest'
			}
		}
    }
}
