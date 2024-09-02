pipeline {
    agent any
    
    environment { 
        registryProd = 'http://192.168.100.224:30273'
        registryTest = 'http://192.168.100.224:30274'
        registryProdTag   = '192.168.100.224:30273'
        registryCredential = 'nexuscred' 
        dockerImage = '' 
        ProdTagImage = ''
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
                    dockerImage = "${params.IMAGE_REGISTRY}/${IMAGE_NAME}:${params.IMAGE_TAG}"
                    echo "Test Docker Image Tag is: ${dockerImage}"
                    docker.withRegistry( "${registryTest}", registryCredential ) { 
                        // docker.image("${dockerImage}").pull()
                        def imageTest = docker.image("${dockerImage}");
                        imageTest.pull()
                    }
                }
            }
        }
        stage('Tag Docker Image') {
            steps {
                script{
                    ProdTagImage = "${registryProdTag}/${IMAGE_NAME}:${params.IMAGE_TAG}"
                    echo "Prod Docker Image Tag is: ${ProdTagImage}"
                    sh "docker tag ${dockerImage} ${ProdTagImage}"
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script{
                    docker.withRegistry( "${registryProd}", registryCredential ) { 
                        def imageProd = docker.image("${ProdTagImage}");
                        imageProd.push()
                    }
                }
            }
        }        
        stage('Remove Docker Image') {
            steps {
                script{
                    sh "docker rmi ${dockerImage} ${ProdTagImage}"                    
                }
            }
        }      
    }
}
