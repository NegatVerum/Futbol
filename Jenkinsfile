pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
// h
	stages {

		stage('Build') {

			steps {
				sh 'docker build -t negatverum/furbol .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push negatverum/furbol'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}