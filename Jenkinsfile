pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/AnupamaSoma/maven-project.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
              sh label: '', script: 'mvn package'
            }
                
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat8(credentialsId: 'mycred', path: '', url: 'http://172.31.81.254:8080')], contextPath: 'testapp', war: '**/*.war'
            }
            
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/AnupamaSoma/FunctionalTesting.git'
      
               sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar '
            }

        }
        stage('ContinuousDelivery')
        {
           steps
           {
               input message: 'Waiting for Approval from the DM!', submitter: 'naresh'
               deploy adapters: [tomcat8(credentialsId: 'mycred', path: '', url: 'http://172.31.29.52:8080')], contextPath: 'prodapp', war: '**/*.war'
           }
        }
    }
    
}
