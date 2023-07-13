pipeline {
    agent {docker {image maven 3.9.3} }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out from SCM'
	        checkout changelog: false, poll: false,
		scm: [$class: 'GitSCM',
		branches: [[name: '*/main']],
		extensions: [], userRemoteConfigs: [[credentialsId: '',
		url: 'https://github.com/dkakandki/Online_book_store.git']]]	
            }
        }
        stage('BUILD + UT') {
            steps {
                echo 'Building and Testing'
		sh 'mvn clean install package'
            }

        }
        stage('deploy') {
            steps {
                echo 'deploy....'
		//sh 'mvn deploy'
            }
        }
    }
    }
