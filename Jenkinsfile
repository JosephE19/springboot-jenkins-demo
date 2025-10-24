pipeline {
	agent any

	stages {
		stage('Checkout') {
			steps {
				echo 'Checking out code from Github...'
				checkout scm
			}
		}

		stage('Build') {
			steps {
				echo 'Building Spring Boot application...'
				sh 'chmod +x mvnw'
				sh './mvnw clean package'
			}
		}

		stage('Test') {
			steps {
				echo 'Running tests...'
				sh'./mvnw clean package'
			}
		}

		stage('Archive') {
			steps {
				echo 'Archiving the JAR file...'
				archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
			}
		}
	}
}
