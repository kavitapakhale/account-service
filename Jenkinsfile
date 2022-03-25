node 
{
  def MAVEN_HOME = tool "mymaven"
   env.PATH = "${env.PATH}:${MAVEN_HOME}/bin"

  
  stage('checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/kavitapakhale/account-service']]])

 stage ('Initial Setup')
     {
          sh 'mvn clean compile'
     }
stage ('Unit Testing')
   {
   sh 'mvn test'
   }

stage('Code Quality Analysis'){
    
    withSonarQubeEnv('kavisonar') 
	    	{
                 sh 'mvn sonar:sonar -Dsonar.organization=kavisonar1 -Dsonar.projectKey=kavisonar1'
		
    		}
  }
}




   
   
