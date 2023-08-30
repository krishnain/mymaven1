pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/krishnain/mymaven1.git'
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
                deploy adapters: [tomcat9(credentialsId: '1de49ba2-3d51-4529-be2e-30dd4e9899dc', path: '', url: 'http://172.31.12.252:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
         stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipleine1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1de49ba2-3d51-4529-be2e-30dd4e9899dc', path: '', url: 'http://172.31.13.158:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
