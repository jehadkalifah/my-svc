pipeline {
    agent any
    
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'Version Variable')
    }
    
    stages {
        stage('Run Docker') {
            steps {
                script{
                    img = 'httpd:2.4-alpine'
                    // Uses docker run to run the image
                    docker.image("${img}").run('-d -p 8090:80')
                }
            }
        }
    }
}
