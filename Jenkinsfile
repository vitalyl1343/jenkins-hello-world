pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/vitalyl1343/go-hello'
            }
        }
        stage('Build') {
            steps {
                sh 'GO111MODULE=off go build'
            }
        }
    }
}
