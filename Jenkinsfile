pipeline{
    agent any
    tools { nodejs "node"}
    stages{
        stage('testing'){
            steps{
                echo "This is test area"
            }
        }

        stage('production'){
            steps{
                echo "Running in the EC2 instance"
                sh '''
                    sudo ssh -t -o StrictHostKeyChecking=no -i /var/lib/jenkins/testnode.pem ubuntu@ec2-13-41-80-52.eu-west-2.compute.amazonaws.com
                    cd /var/www
                    sudo rm -rf html
                    sudo mkdir html
                    cd html
                    sudo git init
                    sudo git remote add origin https://github.com/cyclobold/broomsticks.git
                    sudo git fetch
                    sudo git checkout with-auth-thought-jenkins
                    sudo git pull origin with-auth-thoughts
                    sudo npm install
                    sudo npm run start
                   '''
            }
        }
    }
}