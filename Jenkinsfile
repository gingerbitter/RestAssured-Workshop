pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/shazforiot/nodeapp_test.git'
				//emailext attachLog: true, body: '', subject: 'This is the extended email report', to: 'nandini.priya@brigosha.com'
			}
		}

		stage('Build') {

			steps {
			bat script:'docker build -t priyalava/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
			bat script:'docker login -u priyalava -p Nandini@1234'

			}
		}

		stage('Push') {

			steps {
			bat script:'docker push priyalava/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
		bat script:'docker logout'
		}
	}
    



}
