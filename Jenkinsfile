pipeline
{
    agent any

    tools
    {
        maven 'Maven_3.9.9'
    }
    
    environment
    {
        buildNumber ="${BUILD_NUMBER}"
    }
    stages
    {
        stage('Checkout code from GIThub')
        {
            steps()
            {
                git branch: 'DevopsMay', url: 'https://github.com/PranikTech/maven-web-application.git'
            }
        }

        stage('Build the Artifact')
        {
            steps()
            {
                sh 'mvn clean package'
            }
        }

        stage('Build the docker image')
        {
            steps()
            {
                sh 'docker build -t 047719650789.dkr.ecr.eu-west-2.amazonaws.com/maven-we-application:${buildNumber} .'
            }
        }

        stage('Authenticate and Push docker image to AWS ECR')
        {
            steps()
            {
                sh 'aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 047719650789.dkr.ecr.eu-west-2.amazonaws.com'
                sh 'docker push 047719650789.dkr.ecr.eu-west-2.amazonaws.com/maven-we-application:${buildNumber}'
            }
        }

        stage('Remove the Image from the server')
        {
            steps()
            {
                sh 'docker rmi 047719650789.dkr.ecr.eu-west-2.amazonaws.com/maven-we-application:${buildNumber}'
            }
        }
    } 
}