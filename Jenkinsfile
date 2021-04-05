node {
    stage('continous downlaod') {
    git 'https://github.com/AnupamaSoma/maven-project.git'
}
    stage('continous build') {
    sh 'mvn package'
}
     stage('continous deploy'){
         deploy adapters: [tomcat8(credentialsId: 'mycred', path: '', url: 'http://172.31.81.254:8080')], contextPath: 'testapp', war: '**/*.war'
         //sh 'java -jar /home/ubuntu/.jenkins/workspace/scriped_pipeline/testing.jar '
          }
    stage('continous testing '){
        git 'https://github.com/AnupamaSoma/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriped_pipeline/testing.jar '
    }
    stage('continous deploy')
    {
        deploy adapters: [tomcat8(credentialsId: 'mycred', path: '', url: 'http://172.31.29.52:8080')], contextPath: 'prodapp', war: '**/*.war'
        sh 'echo deployed to tomcat'
        
    }
      stage ('email notification')
     {
        mail bcc: '', body: 'test1', cc: '', from: '', replyTo: '', subject: 'test1', to: 'likithadithyadell@gmail.com'
    }
}

