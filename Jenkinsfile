pipeline {
    agent any 
    
    environment {
        IMAGE_NAME = 'myapp'
        DOCKERFILE_PATH = 'DockerfileMultiStage'
        TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ZoharPerets/maven-hello-world.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.image('docker:24.0.2').inside('-v /var/run/docker.sock:/var/run/docker.sock -e HOME=/home/jenkins') {
                        sh 'mkdir -p $HOME'
                        sh 'docker build -t ${IMAGE_NAME}:${TAG} -f ${DOCKERFILE_PATH} .'
                    }
                }
            }
        }  
    }
    
}
