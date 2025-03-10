pipeline {
    agent any
    stages{
        stage('Checkout') {
            steps {
                git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
            }
        }
        stage('Build') {
            steps {
                dir('springboot-docker') {
                    bat 'mvn clean package'
                }
            }
        }
    }
}
