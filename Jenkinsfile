pipeline {
    agent any

    environment {
  arm_client_id       = "786927cb-2272-4c90-b73d-7c001f69e105"
  arm_client_secret   = "zKS8Q~BYrZQDQKjZWuTbfN9a4xgAbLvEEm3DdbeX"
  arm_tenant_id       = "cce1a4fc-a91d-4308-97f5-342417d7a0db"
  arm_subscription_id = "c039ec6d-860e-4dbe-993f-594f8cd3d99d"

    }

    stages {


        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Approval') {
            steps {
                input message: 'Approve Terraform Apply?'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }

    post {
        success {
            echo 'Azure VM created successfully'
        }
        failure {
            echo 'Terraform execution failed'
        }
    }
}
