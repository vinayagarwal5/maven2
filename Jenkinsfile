node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/vinayagarwal5/maven.git'
    }
     stage('Continuousbuild') 
    {
        sh 'mvn package'
    }
    stage('Continuous Deployment')
    {
        deploy adapters: [tomcat9(credentialsId: '02c6b85e-0232-4146-93e6-85f66d90c6d7', path: '', url: 'http://172.31.24.250:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('Continuous testing')
    {
        git 'https://github.com/vinayagarwal5/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('Continuous Delivery')
    {
        deploy adapters: [tomcat9(credentialsId: '02c6b85e-0232-4146-93e6-85f66d90c6d7', path: '', url: 'http://172.31.28.8:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
}
