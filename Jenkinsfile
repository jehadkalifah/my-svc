pipeline {
    agent any
    
    environment { 
        registryProd = 'http://192.168.100.224:30273'
        registryTest = 'http://192.168.100.224:30274'
        registryProdTag   = '192.168.100.224:30273'
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
                    ProdTagImage = "${registryProdTag}:${params.IMAGE_TAG}"
                    echo "Prod Docker Image Tag is: ${ProdTagImage}"
                    // docker.image("${params.IMAGE_REGISTRY}:${params.IMAGE_TAG}").pull()
                    docker.withRegistry( "${registryTest}", registryCredential ) { 
                        // docker.image("${dockerImage}").pull()
                        def imageTest = docker.image("${dockerImage}");
                        imageTest.pull()
                        // imageTest.imageName("joj")
                    }
                    sh "docker tag ${dockerImage} ${ProdTagImage}"
                }
            }
        }
    }
}
