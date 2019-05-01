pipeline {
    agent {
        docker 'maven:alpine'
    }
    stages {
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
