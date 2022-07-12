node('built-in') 
{
    stage('ContinuousDownload')
    {
          git 'https://github.com/krishnain/mymavenn.git'
    } 
    stage('ContinuousBuild')
    {
         sh 'mvn package'
    } 
    stage('ContinuousDeployment')
    {
         deploy adapters: [tomcat9(credentialsId: '31bf8626-40d6-4c9d-aa6c-87f7a5cf2854', path: '', url: 'http://172.31.2.90:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
         git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
         sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
        
    } 
    stage('ContinuousDelivery')
    {
        input message: 'Need approvals from the DM!', submitter: 'srinivas'
        deploy adapters: [tomcat9(credentialsId: '31bf8626-40d6-4c9d-aa6c-87f7a5cf2854', path: '', url: 'http://172.31.0.146:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
    
    
    
}
