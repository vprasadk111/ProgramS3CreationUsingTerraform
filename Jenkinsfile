pipeline {
  parameters {
    password (name: 'AKIAQ27VBN424JMJSUOK')
    password (name: 'wj58b/1Uj6j4ju71YEoua+ANnnLN7sPA6Yprnloc')
  }
  environment {
    TF_WORKSPACE = '/home/ec2-user/GIT_AZUREDEVOPS/ProgramS3CreationUsingTerraform' //Sets the Terraform Workspace
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
    }
}
