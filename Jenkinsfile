pipeline {
	//agent any
	agent { docker { image 'maven:3.6.3'} }
	stages{
		stage('Build') {
			steps {
				sh "mvn --version"
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
