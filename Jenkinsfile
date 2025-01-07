pipeline {	
	agent any	
	tools {	    
		maven 'my-maven'		
		jdk 'my-java'	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/UST-Training-2025/eureka-service-registry.git', branch:'main'}
		}
		stage('Build'){			
			steps {bat "mvn clean install -DskipTests"}		
		}	
		stage('Pre-Deploy'){
			steps{bat "docker rm -f eureka-cntr"
					bat	"docker rmi -f eureka-img"}
		}	
		stage('Deploy') {			
			steps { bat "docker build -t eureka-img ."			    
			            bat "docker run -p 9761:8761 -d --name eureka-cntr --network my-net eureka-img"}		
		}		
	}
}
