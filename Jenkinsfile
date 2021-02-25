pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Build') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
			}
				
		}
		stage('compile') {
			steps {
				sh "mvn clean compile"
			}
				
		}
		stage('test') {
			steps {
				sh "mvn test"
			}
				
		}
		stage('Integration test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
				
		}

		stage('Build docker image') {
			steps {
				//"docker build -t abounader10/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("abounader10/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
				
		}

		stage('Push docker image') {
			steps {
				script {
					docker.withRegistry('','dockerHub') {
						dockerImage.Push();
						dockerImage.Push('latest');
					}
					
				}
			}
				
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
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
