pipeline
{

	agent any
	
		stages {
				stage ('scm checkout') {
					steps {
						git 'https://github.com/chaitanyapratap19/maven-project.git'
					}
				}



				stage ('code test') {
				       steps {
						withMaven(maven: 'MAVEN_HOME') {
							sh 'mvn test'
						}
				       }	       
				}
			
			     stage ('code package') {
				       steps {
						withMaven(maven: 'MAVEN_HOME') {
							sh 'mvn package'
						}
				       }	       
			      }
			
			
			    stage ('code install') {
				       steps {
						withMaven(maven: 'MAVEN_HOME') {
							sh 'mvn install'
						}
				       }	       
				}
			
			
			
			stage ('ssh tomcat') {
				       steps {
						sshPublisher(publishers: [sshPublisherDesc(configName: 'Tomcat', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/lib/tomcat/webapps', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
				       }	       
			}
			
			
			stage ('deploy to tomcat') {
				steps {
						sshagent (['52.203.20.141']) {
						sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@52.203.20.141:/var/lib/tomcat/webapps'
						}
				}
	
}
				       
	        	}				       

	
}
