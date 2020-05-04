pipeline{
     agent any
    stages{
         stage('Checkout-SCM')
		 {
		     steps{
			            checkout([$class: 'GitSCM', branches: [[name: '*/master']], 
				        doGenerateSubmoduleConfigurations: false, 
				        extensions: [], 
				        submoduleCfg: [],
				        userRemoteConfigs: [[credentialsId: '2a239424-0e74-41e9-8034-488a00f90311',
			            url: 'https://github.com/HariReddy910/isolvers.git']]])
			        }
		   }
	     stage('Build-stage')
		 {
		    steps{
		               sh label: '', script: 'mvn package'
		             }
	     }
		 stage('Deployment')
		 {
		    steps{
                  deploy adapters: [tomcat9(credentialsId: '2a239424-0e74-41e9-8034-488a00f90311',
		path: '', url: 'http://3.21.113.130:8080')], contextPath: 'harindra', war: '**/*.war'		          
		    }
	     }
	    
        }
}
