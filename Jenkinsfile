pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-token')
	}

	stages {

        stage('node_modules') {

			steps {
				// sh 'docker-compose -f docker-compose.prod.yml build'
                sh 'yarn'
			}
		}

		stage('Build') {

			steps {
				// sh 'docker-compose -f docker-compose.prod.yml build'
                sh 'yarn build'
			}
		}

        

		// stage('Login') {

		// 	steps {
		// 		sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
		// 	}
		// }

        stage('test') {

			steps {
				sh 'yarn test'
			}
		}

	}

	post {
		always {
			// sh 'docker logout'
            sh 'executed successfully'
		}
	}

}