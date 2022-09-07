pipeline{
    agent any
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
                    sudo ssh -i -t /var/lib/jenkins/broomsticks.pem -o StrictHostKeyChecking=no ubuntu@ec2-18-132-118-45.eu-west-2.compute.amazonaws.com
                    '''
            }
        }
    }
}