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
              deploy adapters: [tomcat8(credentialsId: '0dcbc181-3592-435c-88c8-8de41abfafb4', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'       
			  }
			  }
			  }
			  }

