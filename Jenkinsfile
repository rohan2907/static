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
                        withAWS(region:'us-east-2', credentials:'github'){
                        s3Upload(file:'index.html', bucket:'elasticbeanstalk-us-east-2-315535007421', path:'index.html')
                    }                             
                }
            }
        }
    }
}
