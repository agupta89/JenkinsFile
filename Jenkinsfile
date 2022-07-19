properties([pipelineTriggers([githubPush()])])
pipeline{
		agent any
	        
	         stages{
	              stage('Dev Code Changes') {
	              
            steps {
                
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'master'], [name: 'STG']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/agupta89/TestDev.git',
                    credentialsId: '',
                 ]]
                ])
            }
	              }
	         stage('Test Code') {
	             
				  steps {
		   echo 'Hello World'
				  script {			    	
                   if ("${env.GIT_BRANCH}" == "master") {
                   env.environment = "master"
		    } else if("${env.GIT_BRANCH}" == "STG"){
                   env.environment = "STG"
		    } else {
                    env.environment = "Dev"
                   }
		    echo env.environment
                }
}
}
}
}
