pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
		stage('Publish to Nexus'){
			steps{
				nexusArtifactUploader artifacts: [[artifactId: 'jenhuDevOpsLab', classifier: '', file: 'target/jenhuDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: 'af458c0a-c0cf-408c-9059-e1279d4a125f', groupId: 'com.jenhudevopslab', nexusUrl: '54.226.163.178:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'jenhuDevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
		}
        // Stage3 : Publish the source code to Sonarqube
        stage('Deploy'){
			steps {
				echo 'deploying...'
			}

        
        
		}

	}
}