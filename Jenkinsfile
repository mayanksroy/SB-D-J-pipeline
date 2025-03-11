pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayanksroy/SB-D-J-pipeline.git'
            }
        }
        // stage('Deploy') {
        //     steps {
        //         echo "Deploying application..."
        //         sh '''
        //             docker build -t myapp:latest .
        //             docker run -d -p 8080:8080 myapp:latest
        //         '''
        //     }
        // }
    }
}
