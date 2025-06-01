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
                sh 'echo "Building..."'
                // Your build commands here
            }
        }
        stage('Deploy') {
            steps {
                sshagent(credentials: ['jenkins-ssh-key']) {
                    sh "scp -o StrictHostKeyChecking=no -r * ubuntu@<13.48.106.33>:/var/www/html/myapp"
                }
            }
        }
    }
}