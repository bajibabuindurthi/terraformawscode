pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/venkatkukatla/AWS-terraform.git']])
            }
        }
        
        stage('version') {
            steps {
                sh 'terraform version'
                
            }
        }

        stage('init') {
            steps {
                sh 'terraform init "-migrate-state" -force-copy'
               
            }
        }

        stage('validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('plan') {
            steps {
                sh 'terraform plan'
            }
        }

         stage('apply') {
             steps {
                 sh 'terraform apply --auto-approve'
             }
         }
    }
}
