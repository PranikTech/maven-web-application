pipeline
{
    agent any

    tools
    {
        maven 'Maven_3.9.9'
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
    } 
}