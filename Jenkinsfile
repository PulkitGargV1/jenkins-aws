pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                  echo “Multiline shell steps works too”
                  ls -lah
               '''
      }
    }
    stage('Test') {
      steps {
        sh 'echo "Hello WorldAgain"'
      }
    }
    stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-1',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacitywebsitehostingbucket')
                  }
         }
              }
  }
}
