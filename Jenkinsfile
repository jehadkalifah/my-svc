pipeline {
    agent any
	environment {
        // define an image tag name
        def img = ("${env.JOB_NAME}:${env.BUILD_ID}").toLowerCase()
        // def prodimage = docker.image("${params.VERSION}")
	// def prodimage = docker.image("nginx:latest")	
    }	
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version Variable')
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Pull Image Name: ${params.VERSION}"
		prodimage = docker.image("nginx:latest").pull()	 
            }
        }
    }
}
