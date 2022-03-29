pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-token')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker-compose -f docker-compose.prod.yml build'
			}
		}

        

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

        stage('test') {

			steps {
				sh 'yarn test'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ndrohith09/app-prod:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}