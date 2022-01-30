pipeline {
    agent any     

    stages {
        stage('Clone Code') {
            steps {
               git branch: 'main', url: 'https://github.com/RajaRajan-P/DevOpsProject.git'
            }
        }
        /* stage('Docker Build'){
            steps{
                sh "docker build . -t prajan0550/my-devops-php-website"
            }
        }
        stage('DockerHub Push'){
            steps{
                
                withCredentials([string(credentialsId: 'DockerPwd', variable: 'dockerPwd')]) {
                      sh "docker login -u prajan0550 -p ${dockerPwd}"
                }
                     sh "docker push prajan0550/my-devops-php-website "
            }
        }
        */
        

          stage('Install docker and its dependencies and run contianer') {
            steps {
               ansiblePlaybook credentialsId: 'Node', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'servers.inv', playbook: 'deployment-playbook.yml'
              /*  sh "sudo su"
                sh "ansible -m ping all -i servers.inv --private-key  /home/ec2-user/DevOpsProject.pem -u ec2-user"
              sh  ansible-playbook deployment-playbook.yml -i servers.inv --private-key  /home/ec2-user/DevOpsProject.pem -u ec2-user
              ansiblePlaybook credentialsId: 'Node', installation: 'ansible', inventory: 'servers.inv', playbook: 'deployment-playbook.yml' */
            }
        } 


    }
}
