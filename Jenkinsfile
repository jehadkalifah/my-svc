pipeline {
    agent any
	environment {
        // define an image tag name
        def img = ("${env.JOB_NAME}:${env.BUILD_ID}").toLowerCase()
        def prodimage = docker.image("${params.VERSION}")
    }	
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version Variable')
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Pull Image Name: ${params.VERSION}"
		id = docker.prodimage.id   
		echo "Image ID is: ${id}"
            }
        }
    }
}
