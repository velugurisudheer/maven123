pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
       stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.40.137:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
      stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
      stage('ContinuousDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.33.74:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
        
    }
}
