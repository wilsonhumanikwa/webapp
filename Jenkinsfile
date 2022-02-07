pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY = credentials('AWS_ACCESS_KEY')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

    stages {
        stage('GitHub Code Checkout') {
            steps {
            checkout scm
            }
        }
        stage ("initialise Terraform") {
            steps {
                sh 'terraform init'
            }
        }
        stage ("format terraform") {
            steps {
                sh 'terraform fmt' 
            }
        }        
        stage ("validate Terraform") {
            steps {
                sh 'terraform validate'
            }
        }
        stage ("Preflight Check") {
            steps {
                sh 'terraform plan' 
            }
        }
                
        stage ("Deploy WebApp") {
            steps {
                echo "Applying Terraform Configuration"
                sh 'terraform apply --auto-approve' 
           }
        }
    }
}