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
				bat 'docker login -u %DOCKERHUB_CREDENTIALS_USR% -p %DOCKERHUB_CREDENTIALS_PSW%'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push negatverum/futbol'
				bat 'docker image prune -a -f'
			}
		}

		// stage('EC2') {

		// 	steps {
		// 		bat 'ssh -i /Users/Usuario/.jenkins/new_ec2_linux.pem ec2-user@ec2-18-144-84-139.us-west-1.compute.amazonaws.com | docker run -d -p 80:80 negatverum/futbol'
		// 	}
		// }

		// stage('EC2') {
        //      steps {
        //          script {
        //              sshagent(credentials : ['ec2-access']) {
        //                 sh "echo pwd"

        //             }
        //         }
        //     }

		// }	
	}

	post {
		always {
			// bat 'exit'
			bat 'docker logout'
		}
	}

}