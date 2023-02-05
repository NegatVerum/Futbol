pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhubCredentials')
	}

	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/furbol .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login --username=%DOCKERHUB_CREDENTIALS_PSW% -p %DOCKERHUB_CREDENTIALS_USR%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/furbol'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}