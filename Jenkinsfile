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
	


		stage('Deploy to Production ') {
			steps {
				timeout(time:5, unit:'DAYS'){
					input message:'Approve Production Deployment qd tu veux !!'
				}
			build job: 'deploy-to-prod'
			}
			post {
			   success {
			   	echo 'Code deployed to Production'
			   }

			   failure {
			   	echo "Code Deployment failed"
				}
			}
		}


	}
		
}		
				
