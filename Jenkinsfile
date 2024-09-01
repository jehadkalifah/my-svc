pipeline {
    agent any
	environment {
        // define an image tag name
        def img = ("${env.JOB_NAME}:${env.BUILD_ID}").toLowerCase()
        def prodimage = docker.image("${params.VERSION}")
	def id = prodimage.id  	
    }	
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version Variable')
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Pull Image Name: ${params.VERSION}"
		echo "Image ID is: ${img}"
		echo "Image ID is: ${id}"
            }
        }
    }
}
