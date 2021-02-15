pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
	environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
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
				script {
                def NexusRepo = Version.endsWith("SNAPSHOT") ? "VinaysDevOpsLab-SNAPSHOT" : "VinaysDevOpsLab-RELEASE"
				nexusArtifactUploader artifacts: 
				[[artifactId: "${ArtifactId}",
				classifier: '', 
				file: 'target/jenhuDevOpsLab-0.0.4-SNAPSHOT.war', 
				type: 'war']], 
				credentialsId: 'af458c0a-c0cf-408c-9059-e1279d4a125f',
				groupId: "${GroupId}", 
				nexusUrl: '54.226.163.178:8081', 
				nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: "${NexusRepo}", 
				version: "${Version}"
				}
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