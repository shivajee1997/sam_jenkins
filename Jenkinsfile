pipeline {
  agent any
 
  stages {
    
    stage('Build') {
      steps {
        sh 'sam build'
        stash includes: '**/.aws-sam/**/*', name: 'aws-sam'
      }
    }
    stage('beta') {
      environment {
        STACK_NAME = 'sam-app-beta-stage'
        S3_BUCKET = 'sam-jenkins-demo-us-east-1-user1'
      }
      steps {
        withAWS(credentials: 'Personla', region: 'us-east-1') {
          sh 'sam deploy --stack-name $STACK_NAME -t template.yaml --s3-bucket $S3_BUCKET --capabilities CAPABILITY_IAM'
        }
      }
    }
    }
  }

