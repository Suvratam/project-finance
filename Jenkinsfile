pipeline {
    agent any
    
    tools {
        maven 'Maven3'
    }
    stages {
        stage('clone code') {
            steps {
                git 'https://github.com/Suvratam/star-agile-banking-finance.git'
            }
        }
        stage('Ansible') {
            steps {
                ansiblePlaybook credentialsId: 'devops', disableHostKeyChecking: true, installation: 'Ansible', playbook: '/var/lib/jenkins/workspace/jen-Ans/app.yml', vaultTmpPath: ''
            }
        }
        
        stage('Maven build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
         stage('Build Image') {
            steps {
                script{
                    sh 'docker build -t suvratam/banking:latest .'
                }
                
            }
         }
            stage('Push Image to docker hub') {
            steps {
                script{
                   sh 'docker push suvratam/banking:latest'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo docker run -itd --name My-first-containe21211 -p 8083:8081 suvratam/banking:latest'
                }
            }
        
    }
}
        
