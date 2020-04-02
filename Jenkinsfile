pipeline {
    agent any
    stages {
	stage('Launch launcher') {
	    steps {
		bat 'python python/dronelauncher_python.py'
            }
	}
    }
    
    post {
        always {
            junit '**/TEST*.xml'
            emailext attachLog: true, attachmentsPattern: '**/TEST*xml',
	    body: 'Bod-DAy!', recipientProviders: [culprits()], subject:
            '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS!'
	}
    }
}
