// pipeline {
//     agent any

//     stages {
//         stage('Checkout') {
//             steps {
//                 git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
//             }
//         }
//     }
// }

pipeline {
    agent any

    environment {
        IMAGE_NAME = "sb-docker-jenkin-pipeline-demo"
        DOCKER_HUB_USER = "mayanksroy"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_HUB_USER/$IMAGE_NAME:latest .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                        sh 'docker push $DOCKER_HUB_USER/$IMAGE_NAME:latest'
                    }
                }
            }
        }
    }
}

