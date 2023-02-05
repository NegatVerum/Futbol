pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
// h
	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/furbol .'
			}
		}

		stage('Login') {

			steps {
				bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
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