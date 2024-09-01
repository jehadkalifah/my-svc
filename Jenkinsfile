pipeline {
    agent any
    
    environment { 
        // registry = "YourDockerhubAccount/YourRepository" 
        registryCredential = 'nexuscred' 
        dockerImage = '' 
    }
    parameters {
        string(name: 'registry', defaultValue: '', description: 'Docker Registry')
        string(name: 'imagetag', defaultValue: '', description: 'Docker Image Tag')
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
                    echo "Docker Image Tag is: ${params.registry}:${params.imagetag}"
                }
            }
        }
    }
}
