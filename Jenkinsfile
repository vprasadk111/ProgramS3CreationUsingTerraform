provider "aws"{
        region="us-east-1"
}

resource "aws_s3_bucket" "terraformawsbucket" {

bucket= "vishnubucket1111111"

}
[ec2-user@ip-172-31-17-40 ProgramS3CreationUsingTerraform]$ cat Jenkinsfile
pipeline {
  parameters {
    password (name: 'AKIAQ27VBN424JMJSUOK')
    password (name: 'wj58b/1Uj6j4ju71YEoua+ANnnLN7sPA6Yprnloc')
  }
  environment {
    TF_WORKSPACE = '/usr/bin/' //Sets the Terraform Workspace
    TF_IN_AUTOMATION = 'true'
    AWS_ACCESS_KEY_ID = "${params.AWS_ACCESS_KEY_ID}"
    AWS_SECRET_ACCESS_KEY = "${params.AWS_SECRET_ACCESS_KEY}"
  }
  stages {
    stage('Terraform Init') {
      steps {
        sh "${env.TERRAFORM_HOME}/terraform init -input=false"
      }
    }
    stage('Terraform Plan') {
      steps {
        sh "${env.TERRAFORM_HOME}/terraform plan -out=tfplan -input=false -var-file='dev.tfvars'"
      }
    }
    stage('Terraform Apply') {
      steps {
        input 'Apply Plan'
        sh "${env.TERRAFORM_HOME}/terraform apply -input=false tfplan"
      }
    }
    stage('AWSpec Tests') {
      steps {
          sh '''#!/bin/bash -l
bundle install --path ~/.gem
bundle exec rake spec || true
'''

        junit(allowEmptyResults: true, testResults: '**/testResults/*.xml')
      }
    }
  }
}
