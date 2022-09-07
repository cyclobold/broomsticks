pipeline{
    agent any
    tools {
        nodejs "node"
    }
    stages{
        stage('test'){
            steps{
                echo "Testing stage"
            }
        }

        stage('production'){
            steps{
                echo "Production stage"
                sh '''
                    sudo ssh -i /var/lib/jenkins/broomsticks.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-18-132-118-45.eu-west-2.compute.amazonaws.com
                    cd /var/www/
                    sudo pm2 kill
                    sudo rm -rf html
                    sudo mkdir html
                    cd html
                    sudo git init
                    sudo git remote add origin https://github.com/cyclobold/broomsticks.git
                    sudo git fetch
                    sudo git checkout with-auth-thoughts
                    sudo git pull origin with-auth-thoughts
                    sudo npm install
                    sudo PORT=3000 pm2 start ./bin/www
                    '''
            }
        }
    }
}