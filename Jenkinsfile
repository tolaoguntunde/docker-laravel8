pipeline {
    agent any
    stages {
        stage('buildphpimage') {
            steps {
                sh 'git clone https://github.com/tolaoguntunde/docker-laravel8'
                dir('docker-laravel8') {
                    pwd()
                    sh 'docker build -t tolaoguntunde/laravelapp .'
                    sh 'docker run -d -p 9000:80 tolaoguntunde/laravelapp'
                    
                }
            }
        }
        
        stage('uploadImageToDocker') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerID', passwordVariable: 'DOCKERPASSWORD', usernameVariable: 'DOCKERUSER')]) {
                sh'docker login -u $DOCKERUSER -p $DOCKERPASSWORD'
                sh 'docker push tolaoguntunde/laravelapp'
                }
                
            }
        }
        stage('runApplication') {
            steps {
                sh 'docker run -d -p 9000:80 tolaoguntunde/laravelapp'
                echo 'My first deployment successful'
            }
        }
    }
}
