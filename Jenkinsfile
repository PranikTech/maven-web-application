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
                'sh docker build -t 047719650789.dkr.ecr.eu-west-2.amazonaws.com/maven-we-application:${buildNumber} .'
            }
        }
    } 
}