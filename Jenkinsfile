pipeline {
    agent any
    tools {
        // Define a custom Maven tool named 'local_maven' pointing to the installed Maven in Jenkins
        maven 'local_maven'
    }
    
    stages {
        stage ('Build') {
            steps {
                // Use 'mvn' directly since we're relying on the local Maven installation configured above
                sh 'mvn clean package'
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
                // Add deployment steps here
            }
        }
    }
}
