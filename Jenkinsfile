pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
               git branch: 'main', url: 'https://github.com/RajaRajan-P/DevOpsProject.git'
            }
        }
        stage('Docker Build'){
            steps{
                sh "docker build . -t rajarajan/my-devOps-php-website"
            }
        }
        stage('DockerHub Push'){
            steps{
                
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerPwd')]) {
                      sh "docker login -u prajan0550 -p ${dockerPwd}"
                }
                
                sh "docker push rajarajan/my-devOps-php-website "
            }
        }

         stage('Install docker and its dependencies and run contianer') {
            steps {
               ansiblePlaybook credentialsId: 'test-server', installation: 'ansible', inventory: 'servers.inv', playbook: 'deployment-playbook.yml'
            }
        }
    }
}
