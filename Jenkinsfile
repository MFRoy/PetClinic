pipeline{
    agent any
    environment{
        DATABASE_URI = credentials('DATABASE_URI')
        DOCKERHUB_CREDENTIALS = credentials('DOCKERHUB_CREDENTIALS')
        AZ_CREDENTIALS = credentials('AZ_CREDENTIALS')
    }
    stages{
        stage('Install Requirements'){
            steps{
                sh "bash scripts/install.sh"
            }
        }
        stage('Testing'){
            steps{
                sh "bash scripts/test.sh"
            }
        }   
        stage('Build Images'){
            steps{
                sh "bash scripts/build.sh"
            }
        }
        stage('Terraform'){
            steps{
                sh "bash scripts/terraform.sh"
            }
        }
        stage('Deploy'){
            steps{
                sh "bash scripts/k8s.sh"
            
            }
        }
    }
}