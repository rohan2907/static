pipeline{
        agent any
        stages {
            stage('Lint HTML'){
                steps {
                    sh 'tidy -q -e *.html'
                }
            }
            stage('Upload to AWS') {
                steps {
                    retry(3){
                        withAWS(region:'us-east-2', credentials:'aws-static'){
                        s3Upload(file:'index.html', bucket:'arn:aws:s3:::elasticbeanstalk-us-east-2-315535007421', path:'index.html')
                    }                             
                }
            }
        }
    }
}
