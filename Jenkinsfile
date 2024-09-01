pipeline {
    agent any
    
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version Variable')
    }

    stages {
        stage('Pull Docker Image') {
            steps {
                script{
                    img = "${params.VERSION}"
                    // Uses docker run to run the image
                    // docker.image("${img}").run('-d -p 8090:80')
                    imgpull = docker.image("${img}").pull()
                    echo "imgpull.id"
                }
            }
        }
    }
}
