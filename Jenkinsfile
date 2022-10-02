pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('doc-access-final')
    }
    
    stages {
         stage('Build') {
             steps {
                 sh 'docker build -t msravankumar/srav_private_docker_hub:latest .'
             }
        }
        stage('Trivy Scan for Build') {
            steps {
                sh 'trivy image msravankumar/srav_private_docker_hub:latest'
            }
        }
		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push msravankumar/srav_private_docker_hub:latest'
			}
		}
            stage("Talisman Scan"){
            steps{
            sh "curl https://thoughtworks.github.io/talisman/install.sh > ~/install-talisman.sh"
            sh "chmod +x ~/install-talisman.sh"
            sh "~/install-talisman.sh"
            sh "git push -u origin main "
            }
	  }
    }
}
