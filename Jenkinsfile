pipeline{

	agent any

	// environment {
	// 	DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	// }

	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/furbol .'
			}
		}

		// stage('Login') {

		// 	steps {
		// 		bat 'docker login'
		// 	}
		// }

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