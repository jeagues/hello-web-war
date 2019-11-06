pipeline {	
	agent any
	
	stages {
		stage('Init') {
			steps {
				echo "Testing ..."
				}
			}
			
		stage('Build') {
			steps {
				echo "Building via maven..."
				bat 'mvn clean package'
				}
			post {
				succes {
						echo 'Now archiving ...'
						archiveArtifacts artifacts: '**/target/*.war'
						}
				}
			}
			
		stage('Deploy') {
			steps {
				echo "Code Deployed ..."
				}
			}
	}
		
}		
				
