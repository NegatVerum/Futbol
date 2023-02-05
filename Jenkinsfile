pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS_PSW='120096147'
		DOCKERHUB_CREDENTIALS_USR='negatverum'
	}

	stages {

		stage('Build') {

			steps {
				bat 'docker build -t negatverum/futbol:1.0.0-%BUILD_ID% .'
			}
		}

		stage('Login') {

			steps {
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_USR% -p %DOCKERHUB_CREDENTIALS_PSW%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/futbol:1.0.0-%BUILD_ID%'
				// bat 'docker-compose down'
				// bat 'docker image prune -a -f'
			}
		}

		// stage('Pull') {

		// 	steps {
		// 		bat 'docker pull negetverum/futbol'
		// 		// bat 'docker '
		// 	}
		// }
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}