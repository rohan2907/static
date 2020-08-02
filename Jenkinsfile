pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        echo 'Hello Word'
      }
    }
stage('Upload to AWS.') {
                steps {
                    withAWS(region:'us-east-2',credentials:"aws-static") {
                        s3Upload(file:'index.html', bucket:'arn:aws:s3:::elasticbeanstalk-us-east-2-315535007421', path:'index.html')
                    }
                }
  }
}
