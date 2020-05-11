pipeline {
    agent any
    stages {
	stage('Checkout') {
	    steps {
		git 'https://github.com/Q2MORY17/SSRS-Drone-Launcher-Beta'
	    }
	}
	stage('robot -d') {
	    steps {
		dir("test/manual/robot") {
		    sh 'robot -d results pitch.robot'
		}
	    }
	}
	stage('run_tests.sh') {
	    steps {
		dir("test/manual/robot") {
		    sh 'resources/run_tests.sh pitch.robot'
		}
	    }
	}
	stage('Unit test') {
	    steps {
		sh 'cd test/manual/unittest/'
		sh 'python3 -m pytest -v -s test*.py'
	    }
	}
    }
}