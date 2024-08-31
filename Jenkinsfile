pipeline {
    agent any
	environment {
        // define an image tag name
        def img = ("${env.JOB_NAME}:${env.BUILD_ID}").toLowerCase()
    }	

    stages {
        stage('Checkout') {
            steps {
                echo "Building our image"
            }
        }
        stage('Build') {
            steps {
				echo "Building our image"
            }
        }
        stage('Deploy Run') {
            steps {
				echo "Deploy and Run"
            }
        }
        stage('Do Some Tests') {
            steps {
				echo "Do Some tests"
            }
        }
    }
}
