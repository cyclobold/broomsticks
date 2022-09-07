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
                    ssh -t -o StrictHostKeyChecking=no -i /var/lib/jenkins/sampleone.pem ubuntu@ec2-13-40-194-180.eu-west-2.compute.amazonaws.com

                   '''
            }
        }
    }
}