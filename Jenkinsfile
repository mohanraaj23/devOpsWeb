pipeline {
	agent any
	
	stages {
		stage ('Build') {
			steps {
					sh 'mvn clean package'
			}
			
		post {
			success {
				echo "Archiving the Artifacts"
				archiveArtifact artifact: '**/target/*.war'
				}
				
			}
		}
		stage(Deploy to tomcat server'){
		steps{
		deploy adapters: [tomcat7(credentialsId: '1e7c9289-1067-4be7-abdc-2a686caf1e94', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
			}
		}
	}
	
}
