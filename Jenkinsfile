pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                 git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                 sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.16.253:/var/lib/tomcat10/webapps/mytestapp.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.26.142:/var/lib/tomcat10/webapps/myprodapp.war'
            }
        }
    }
}
