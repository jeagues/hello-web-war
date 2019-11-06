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
				success{
						echo 'Now archiving ...'
						archiveArtifacts artifacts: '**/target/*.war'
						}
				}
			}
			
		stage('Deploy to staging ') {
			steps {
				echo "Code Deployed ..."
				build job: 'deploy-to-staging'
				}
			}
	}
		
}		
				
