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
    sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war \
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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'c0bd6fb5-41b6-4c37-ac4a-07f146b25b33', path: '', url: 'http://20.81.224.134:8080')], contextPath: 'Decprodapp', war: '**/*.war'
            }
        }
    }
}
