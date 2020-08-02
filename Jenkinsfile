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
                        withAWS(region:'us-east-2'){
                        s3Upload(file:'index.html', bucket:'elasticbeanstalk-us-east-2-315535007421', path:'https://elasticbeanstalk-us-east-2-315535007421.s3.us-east-2.amazonaws.com/index.html')
                    }                             
                }
            }
        }
    }
}
