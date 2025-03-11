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

    tools {
        maven 'Maven3'  // Ensure 'Maven3' is configured in Jenkins Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package -DskipTests'  // Ensure Maven is installed and configured in Jenkins
            }
        }
    }
}
