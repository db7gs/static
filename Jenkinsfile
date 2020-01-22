pipeline {
    agent any
    stages {
       stage('Lint HTML') {
             steps {
                 sh 'tidy -1 -3 *.html'  
             }
        }
        stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-east-2',credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS credentials"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacityproject4')
                 }
             }
        }
    }
}
