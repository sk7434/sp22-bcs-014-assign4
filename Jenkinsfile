pipeline {
    agent any
    stages {
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
                        ssh -i ~/.ssh/deploy_key -o StrictHostKeyChecking=no ubuntu@13.48.106.33 \
                            "mkdir -p /var/www/html/myapp"
                        rsync -avz -e "ssh -i ~/.ssh/deploy_key -o StrictHostKeyChecking=no" \
                            * ubuntu@13.48.106.33:/var/www/html/myapp/
                    '''
                }
            }
        }
    }
}