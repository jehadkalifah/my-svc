pipeline {
    agent any
    
    environment { 
        // registry = "YourDockerhubAccount/YourRepository" 
        registryCredential = 'nexuscred' 
        dockerImage = '' 
    }
    parameters {
        // ${trigger.artifacts[0].name}
        string(name: 'IMAGE_REGISTRY', defaultValue: '', description: 'Docker Registry')
        // ${trigger.artifacts[0].version}
        string(name: 'IMAGE_TAG', defaultValue: '', description: 'Docker Image Tag')
    }

    stages {
        stage('Pull Docker Image') {
            steps {
                script{
                    // img = "${params.VERSION}"
                    // Uses docker run to run the image
                    // docker.image("${img}").run('-d -p 8090:80')
                    // imgpull = docker.image("${img}").pull()
                    // docker.image("${img}").tag(["192.168.100.224:30274/nginx:latest"])
                    dockerImage = "${params.IMAGE_REGISTRY}:${params.IMAGE_TAG}"
                    echo "Docker Image Tag is: ${dockerImage}"
                    // docker.image("${params.IMAGE_REGISTRY}:${params.IMAGE_TAG}").pull()
                    docker.withRegistry( 'http://192.168.100.224:30274', registryCredential ) { 
                        docker.image("${dockerImage}").pull()
                    }
                }
            }
        }
    }
}
