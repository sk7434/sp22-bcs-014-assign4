pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building application..."'
                // Add your actual build commands here
                // Example for a Node.js app:
                // sh 'npm install'
                // sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                    echo "Deploying to local server..."
                    sudo mkdir -p /var/www/html/myapp
                    sudo chown -R jenkins:jenkins /var/www/html/myapp
                    cp -r * /var/www/html/myapp/
                    echo "Deployment completed successfully to /var/www/html/myapp"
                '''
            }
        }
    }
}