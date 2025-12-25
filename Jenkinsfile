pipeline
{
    agent any
    stages
    {
      stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('continuosBuild')
        {
                steps
                {
                  sh 'mvn package'
                }
            }
            stage('continuousDeployement')
            {
                steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'eda11645-e40d-47ea-8569-c02a15c41e9d', path: '', url: 'http://48.221.112.192:8080/Dectestapp')], contextPath: 'Dectestapp', war: '**/*.war'
            }
            }
            stage('ContinuousTesting')
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
                    deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'eda11645-e40d-47ea-8569-c02a15c41e9d', path: '', url: 'http://20.213.185.100:8080/Decprodapp')], contextPath: 'Decprodapp', war: '**/*.war'
                }
            }
        }
    }
