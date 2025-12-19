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
        stage('continuousbuild'){
            steps{
                sh 'mvn package'
            }
        }
        stage('continuousdeployement')
        {
            steps
            {
    sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war 
azureuser@74.179.96.25:/var/lib/tomcat10/webapps/Dectestapp.war'

            }
        }
        stage('Continuoustesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
                sh '''scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war \azureuser@20.81.224.134:/var/lib/tomcat10/webapps/Decprodapp.war'''
            }
        }
    }
}
