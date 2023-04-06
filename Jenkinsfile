pipeline {
    agent any
    
    stages {
        stage('Clone repository') {
            steps {
                echo 'Cloning files from git...'
                git branch: 'master', f46a5444-2c2e-45ac-af2f-8339f0395be8: 'CloudResume', url: 'https://github.com/yourusername/CloudResume_Frontend.git'
            }
        }
        stage('Push to S3') {
            environment {
                AWS_DEFAULT_REGION = 'us-east-1'
                S3_BUCKET = 'cloudresume-frontend'
            }
            steps {
                sh 'aws s3 sync . s3://${S3_BUCKET} --delete'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
