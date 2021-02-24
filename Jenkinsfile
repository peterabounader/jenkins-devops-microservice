pipeline {
	agent any
	stages{
		stage('Build') {
			steps {
				echo "Build"
			}
				
		}
		stage('test') {
			steps {
				echo "test"
			}
				
		}
		stage('Integration test') {
			steps {
				echo "Integration test"
			}
				
		}
	} 
	post {
		always {
			echo ' i run always'
		}
		success {
			echo ' i run when success'
		}
		failure {
			echo ' i run when failed'
		}
	}
	
}
