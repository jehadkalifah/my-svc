pipeline {
    agent any
	environment {
        // define an image tag name
        // def img = ("${env.JOB_NAME}:${env.BUILD_ID}").toLowerCase()
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
		// docker.image("nginx:latest").pull()	 
		img = 'httpd:2.4-alpine'
                docker.image("${img}").run('-d -p 8090:80')    
            }
        }
    }
}
