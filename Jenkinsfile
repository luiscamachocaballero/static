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
                 withAWS(region:'us-east-1',credentials:'AKIA2SDZ7DXB62V5G4EU') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
                 }
             }
        }
    }
}    
