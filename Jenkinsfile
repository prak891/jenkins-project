pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'echo Build successful'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo All tests passed'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                sh './deploy-staging.sh'
            }
        }
        stage('Approval') {
            steps {
                input 'Approve Deployment to Production?'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                sh './deploy-prod.sh'
            }
        }
    }
    post {
        failure {
            echo 'Pipeline failed. Sending alert...'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}

