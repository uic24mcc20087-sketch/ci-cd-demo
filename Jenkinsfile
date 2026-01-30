pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/uic24mcc20087-sketch/ci-cd-demo.git',
                    branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ci-cd-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop ci-cd || true
                docker rm ci-cd || true
                docker run -d -p 3000:3000 --name ci-cd ci-cd-demo
                '''
            }
        }
    }
}
