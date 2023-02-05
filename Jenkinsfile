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

		stage('Pull') {

			steps {
				bat 'ssh -i /Users/Dante/.jenkins/new_ec2_linux.pem ec2-user@ec2-18-144-84-139.us-west-1.compute.amazonaws.com'
				bat 'docker pull negatverum/futbol:1.0.0-%BUILD_ID%'
				bat 'docker stop $(docker ps -a -q)'
				bat 'docker run -d -p 80:80 negatverum/futbol:1.0.0-%BUILD_ID%'
				bat 'exit'
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