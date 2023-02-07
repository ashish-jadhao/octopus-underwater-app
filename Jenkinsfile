pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                script{
                 app = docker.build("underwater")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Push') {
            steps {
                script{
                        docker.withRegistry('https://292602749294.dkr.ecr.ap-south-1.amazonaws.com/underwater', 'ecr:ap-south-1:aws-credentials') {
                    app.push("${env.BUILD_NUMBER}")        
                    app.push("latest")
                    }
                }
            }
        }

    }
}
