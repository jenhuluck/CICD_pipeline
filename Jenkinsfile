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
				nexusArtifactUploader artifacts: [[artifactId: 'jenhuDevOpsLab', classifier: '', file: 'target/jenhuDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: '', groupId: 'com.jenhudevopslab', nexusUrl: '172.20.10.42:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'jenhuDevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
			}
		}
        // Stage3 : Publish the source code to Sonarqube
        stage('Deploy'){
			steps {
				echo 'deploying...'
			}

        
        
		}

	}
}