pipeline {
    agent any

    stages {
        stage('buildphpimage') {
            steps {
                sh 'git clone https://github.com/tolaoguntunde/docker-laravel8'
                dir('docker-laravel8') {
                    pwd()
                    sh 'docker build -t myimage .'
                    sh 'docker run -d -p 9000:80 myimage'
                    
                }
            }
        }
        stage('uploadImage') {
            steps {
                sh 'docker login '
            }
    // some block
}
    }
}
