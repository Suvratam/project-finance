pipeline {
    agent any
    stages{
        stage('git clone'){
            steps{
                git url:'https://github.com/Suvratam/project-finance/', branch: "master"
              
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t suvratam/staragileprojectfinance:v1 .'
                    sh 'docker images'
                }
            }
        }
         
        
     stage('Deploy') {
            steps {
                sh 'sudo docker run -itd --name My-first-containe21211 -p 8083:8081 suvratam/staragileprojectfinance:v1'
                  
                }
            }
        
    }
}
