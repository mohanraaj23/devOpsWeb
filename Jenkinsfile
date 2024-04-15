pipeline {
    agent any
    tools {
        // Define a custom Maven tool named 'local_maven' pointing to the installed Maven in Jenkins
        maven 'local_maven'
    }
    
    stages {
        stage ('Build') {
            steps {
                // Use 'bat' instead of 'sh' to execute commands on Windows
                bat 'mvn clean package'
            }
            
            post {
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts '**/target/*.war'
                }
            }
        }
        stage('Deploy to Tomcat server') {
            steps {
                deploy adapters: [tomcat7(credentialsId: '1e7c9289-1067-4be7-abdc-2a686caf1e94', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
		
            }
        }
    }
}
