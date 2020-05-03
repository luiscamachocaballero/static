pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world"'
                sh '''
                    echo "multiline shell steps works too"
                    ls -lah
               '''
            }
        }
    	stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-east-1',credentials:'851B4CD6A6A27A43') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
                 }
             }
        }
    }
}    
