pipeline {
    agent any
    stages {
	stage('Checkout') {
	    steps {
		git 'https://github.com/Automan74/Auto.git'
	    }
	}
	stage('robot -d') {
	    steps {
		dir("test/manual/robot") {
		    sh 'robot -d results lift.robot'
		}
	    }
	}
	stage('run_tests.sh') {
	    steps {
		dir("test/manual/robot") {
		    sh 'resources/run_tests.sh lift.robot'
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