pipeline {
  agent any
 
  stages {
    
    stage('Build') {
      steps {
        sh '/usr/local/aws-sam-cli/current/dist/sam build'
      }
    }
    stage('beta') {
      environment {
        STACK_NAME = 'sam-app-beta-stage'
        S3_BUCKET = 'sam-jenkins-demo-us-east-1-user1'
      }
      steps {
        withAWS(credentials: 'Personla', region: 'us-east-1') {
          sh '/usr/local/aws-sam-cli/current/dist/sam deploy --stack-name $STACK_NAME --resolve-s3 venkata_jenk_sam_Second -t template.yaml --capabilities CAPABILITY_IAM'
        }
      }
    }
    }
  }

