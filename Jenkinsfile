pipeline{
	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-node')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t ahmetaslan/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ahmetaslan/node:latest'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}
}