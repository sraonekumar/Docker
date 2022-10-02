pipeline {
environment {
registry = "msravankumar/srav_private_docker_hub" 
registryCredential = 'doc-hub'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/sraonekumar/Docker.git'
}
}
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
}
}
