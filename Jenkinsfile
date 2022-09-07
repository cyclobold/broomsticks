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

                   '''
            }
        }
    }
}