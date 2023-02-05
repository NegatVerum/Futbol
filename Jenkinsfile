pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS_PSW='120096147'
		DOCKERHUB_CREDENTIALS_USR='negatverum'
	}

	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/Futbol .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_PSW% -p %DOCKERHUB_CREDENTIALS_USR%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/Futbol'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}