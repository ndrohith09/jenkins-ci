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
            echo "This block always runs."
        }
        changed {
            echo "This block runs when the current status is different than the previous one."
        }
        fixed {
            echo "This block runs when the current status is success and the previous one was failed or unstable."
        }
        regression {
            echo "This block runs when the current status is anything except success but the previous one was successful."
        }
        unstable {
            echo "This block runs if the current status is marked unstable."
        }
        aborted {
            echo "This block runs when the build process is aborted."
        }
        failure {
            echo "This block runs when the build is failed."
        }
        success {
            echo "This block runs when the build is succeeded."
        }
        unsuccessful {
            echo "This block runs when the current status is anything except success."
        }
        cleanup {
            echo "This block always runs after other conditions are evaluated."
        }
    }

}


 