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
        // ${trigger.registry}
        string(name: 'IMAGE_REGISTRY', defaultValue: '', description: 'Docker Registry')
        // ${trigger.repository}
        string(name: 'IMAGE_NAME', defaultValue: '', description: 'Docker Image Name')
        // ${trigger.tag}
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
                    dockerImage = "${params.IMAGE_REGISTRY}/${IMAGE_NAME}:${params.IMAGE_TAG}"
                    ProdTagImage = "${registryProdTag}/${IMAGE_NAME}:${params.IMAGE_TAG}"
                    echo "Prod Docker Image Tag is: ${ProdTagImage}"
                    // docker.image("${params.IMAGE_REGISTRY}:${params.IMAGE_TAG}").pull()
                    docker.withRegistry( "${registryTest}", registryCredential ) { 
                        // docker.image("${dockerImage}").pull()
                        def imageTest = docker.image("${dockerImage}");
                        imageTest.pull()
                        // imageTest.imageName("joj")
                    }
                    sh "docker tag ${dockerImage} ${ProdTagImage}"
                    docker.withRegistry( "${registryProd}", registryCredential ) { 
                        // docker.image("${dockerImage}").pull()
                        def imageProd = docker.image("${ProdTagImage}");
                        imageProd.push()
                        // imageTest.imageName("joj")
                    }
                    sh "docker rmi ${dockerImage} ${ProdTagImage}"
                }
            }
        }
    }
}
