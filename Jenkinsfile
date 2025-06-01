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
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([sshUserPrivateKey(
                    credentialsId: 'jenkins-ssh-key', 
                    keyFileVariable: 'SSH_KEY',
                    usernameVariable: 'SSH_USER'
                )]) {
                    sh '''
                        mkdir -p ~/.ssh
                        chmod 700 ~/.ssh
                        cp $SSH_KEY ~/.ssh/deploy_key
                        chmod 600 ~/.ssh/deploy_key
                        rsync -avz -e "ssh -i ~/.ssh/deploy_key -o StrictHostKeyChecking=no" * ubuntu@13.48.106.33:/var/www/html/myapp/
                    '''
                }
            }
        }
    }
}