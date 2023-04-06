pipeline {
    agent any
    
    stages {
        stage('Clone repository') {
            steps {
                echo 'Cloning files from git...'
                git branch: 'master', credentialsId: 'CloudResume', url: 'https://github.com/yourusername/CloudResume_Frontend.git'
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