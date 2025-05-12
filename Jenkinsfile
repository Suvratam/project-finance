pipeline {
    agent any
    
    tools {
        maven 'Maven3'
    }
    stages {
        stage('clone code') {
            steps {
                git 'https://github.com/RoshanJajware/star-agile-banking-finance.git'
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
                    sh 'docker build -t roshanrajjajware/banking:latest .'
                }
                
            }
         }
            stage('Push Image to docker hub') {
            steps {
                script{
             
                   sh 'docker push roshanrajjajware/banking:latest'
