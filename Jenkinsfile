
node
{
  
 def mavenHome = tool name: "M3.8.1" 
 stage('CheckoutCode')
 	{
   	git branch: 'development', url: 'https://github.com/kvinayreddy/maven-web-application.git'
 	}
 stage('Build')
 	{
 sh "${mavenHome}/bin/mvn clean package"
 	}
  
  stage('ExecuteSonarQubeReport')
    {
	sh "${mavenHome}/bin/mvn sonar:sonar"
	}
   stage('UploadArtifcatintoNexus')
    {
	sh "${mavenHome}/bin/mvn deploy"
	}
	/*
  stage('DeployToTomcat')
	{
	    sshagent(['4fc4760b-66ca-48b7-8e83-997354ce002c']) {
	    sh "scp -o StrictHostKeyChecking=no target/maven-web-apllication.war vinay@35.231.156.37:/opt/tomcat9/webapps/"
     	}
	}
  */
}
