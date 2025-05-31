pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                url: 'https://github.com/sk7434/sp22-bcs-014-assign4.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building the application..."'
                // Add your actual build commands here
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying to server..."'
                // Add deployment commands here
            }
        }
    }
}