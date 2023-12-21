pipeline {
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME= tool 'sonar-scanner'
    }
    stages {
       stage('CODE COMPILE') {
			steps {
				sh "mvn clean compile"
			}
		}
	
	    stage('SONARQUBE ANALYSIS') {
			steps {
				withSonarQubeEnv('sonar-scanner') {
				sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Devops-CICD \
				-Dsonar.java.binaries=. \
				-Dsonar.projectKey=Devops-CICD '''
				}  
			}
	    }
    }
}
