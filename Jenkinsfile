pipeline
{
    agent any
    stages
    {
        stage('continuousDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
 
        
    }
}
