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

	// 	stage('login aws-ec2'){
    //      steps{
    //         sshagent(credentials:['ec2-user']){\
	// 			bat 'ssh  -o StrictHostKeyChecking=no  ec2-user@ec2-18-144-84-139.us-west-1.compute.amazonaws.com uptime "whoami"'
    //            	// sh 'docker image prune -af'
	// 			// sh 'docker pull negatverum/futbol:1.0.0-%BUILD_ID%'
	// 			// sh 'docker container prune -f'
	// 			// sh 'docker run -d -p 8080:80 negatverum/futbol:1.0.0-%BUILD_ID%'
    //       }
    //     echo "success lgoin"
    //      }
    //    }

		// stage('Pull') {

		// 	steps {
		// 		bat 'ssh -i /Users/Dante/.jenkins/new_ec2_linux.pem ec2-user@ec2-18-144-84-139.us-west-1.compute.amazonaws.com'
		// 		bat 'docker image prune -af'
		// 		bat 'docker pull negatverum/futbol:1.0.0-%BUILD_ID%'
		// 		bat 'docker container prune -f'
		// 		bat 'docker run -d -p 8080:80 negatverum/futbol:1.0.0-%BUILD_ID%'
		// 		bat 'exit'
		// 	}
		// }
	}

	post {
		always {
			// bat 'exit'
			bat 'docker logout'
		}
	}

}