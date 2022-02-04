pipeline {
    agent any

    stages {
        stage('GitHub Code Checkout') {
            steps {
            checkout scm
            }
        }
        stage ("initialise Terraform") {
            steps {
                sh 'terraform init -reconfigure'
                 sh 'echo Hello World 2022 again'
            }
        }
        stage ("format terraform") {
            steps {
                sh 'terraform fmt' 
            }
        }        
        stage ("validate Terraform") {
            steps {
                sh ('terraform validate') 
            }
        }
        stage ("Preflight Check") {
            steps {
                sh ('terraform plan') 
            }
        }
                
        stage ("Deploy WebApp") {
            steps {
                echo "Applying Terraform Configuration"
                sh ('terraform apply --auto-approve') 
           }
        }
    }
}