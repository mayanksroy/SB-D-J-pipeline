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

// pipeline {
//     agent any

//     tools {
//         maven 'Maven3'  // Ensure 'Maven3' is configured in Jenkins Global Tool Configuration
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
//             }
//         }

//         stage('Build with Maven') {
//             steps {
//                 bat 'mvn clean package -DskipTests'  // Ensure Maven is installed and configured in Jenkins
//             }
//         }
//     }
// }

pipeline {
    agent any

    tools {
        maven 'Maven3'  // Ensure 'Maven3' is configured in Jenkins Global Tool Configuration
    }

    environment {
        IMAGE_NAME = 'springboot-app-docker-jenkins-pipeline'  // Docker image name
        CONTAINER_NAME = 'springbootdockercontainer'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat """
                        docker build -t ${IMAGE_NAME}:latest .
                    """
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat """
                        docker stop ${CONTAINER_NAME} || true
                        docker rm ${CONTAINER_NAME} || true
                        docker run -d --name ${CONTAINER_NAME} -p 6060:8080 ${IMAGE_NAME}:latest
                    """
                }
            }
        }
    }
}
