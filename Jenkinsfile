node('built-in') 
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/krishnain/mymaven1.git'
    }
    stage('ContinuousBuild')
    {
       sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
       deploy adapters: [tomcat9(credentialsId: '1de49ba2-3d51-4529-be2e-30dd4e9899dc', path: '', url: 'http://172.31.12.252:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    
        sh 'java -jar  /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '1de49ba2-3d51-4529-be2e-30dd4e9899dc', path: '', url: 'http://172.31.13.158:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
    
}
