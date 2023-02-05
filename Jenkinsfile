pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS_PSW='120096147'
		DOCKERHUB_CREDENTIALS_USR='negatverum'
	}

	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/futbol .'
			}
		}

		stage('Login') {

			steps {
				echo DOCKERHUB_CREDENTIALS_PSW
				echo DOCKERHUB_CREDENTIALS_USR
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_PSW% -p %DOCKERHUB_CREDENTIALS_USR%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/futbol'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}