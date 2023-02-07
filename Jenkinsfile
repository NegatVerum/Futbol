pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS_PSW='123456789'
		DOCKERHUB_CREDENTIALS_USR='negatverum'
	}



	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/futbol:latest .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_USR% -p %DOCKERHUB_CREDENTIALS_PSW%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/futbol:latest'
				bat 'docker image prune -a -f'
			}
		}	
	}

	post {
		always {
			// bat 'exit'
			bat 'docker logout'
		}
	}

}