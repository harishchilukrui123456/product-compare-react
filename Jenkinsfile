pipeline {
    agent any
    
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from your version control system (e.g., Git)
                git branch: 'master', url: 'https://github.com/harishchilukrui123456/product-compare-react.git'
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Node.js and npm if necessary
                sh 'npm install' // or yarn install if you use yarn
            }
        }
        
        stage('Build') {
            steps {
                // Build your React app
                sh 'npm run build' // or yarn build
            }
        }
        
        stage('Test') {
            steps {
                // Run tests if you have any
                sh 'npm test' // or yarn test
            }
        }
        
        stage('Deploy') {
            steps {
                // Deploy your React app to your hosting platform (e.g., AWS S3, Netlify, etc.)
                // Example: Deploy to AWS S3
                sh '''
                    aws s3 sync build/ bucketname
                '''
                // Replace 'your-bucket-name' and 'your-distribution-id' with your AWS details
            }
        }
    }
    
    post {
        always {
            // Clean up workspace after pipeline execution
            cleanWs()
        }
        
        success {
            // Send notification on success if needed (e.g., Slack, Email)
            echo 'React app deployment successful'
        }
        
        failure {
            // Send notification on failure if needed (e.g., Slack, Email)
            echo 'React app deployment failed'
        }
    }
}

