pipeline {
    agent {
        docker {
            image 'maven:3.8.7-openjdk-17'
        }
    }
    environment {
        IMAGE_NAME = 'springboot-jenkins-docker'
        CONTAINER_NAME = 'springapp'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-repo-url.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker stop ${CONTAINER_NAME} || true'
                sh 'docker rm ${CONTAINER_NAME} || true'
                sh 'docker run -d --name ${CONTAINER_NAME} -p 8080:8080 ${IMAGE_NAME}'
            }
        }
    }
}
