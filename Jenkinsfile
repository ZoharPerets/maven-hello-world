pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17-alpine' // Docker image to use
            
        }
    }
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
                    docker.build("${IMAGE_NAME}:${TAG}", "-f ${DOCKERFILE_PATH} .")
                }
            }
        }  
    }
    
}
