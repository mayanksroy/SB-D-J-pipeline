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
    }
}

