pipeline {

    agent any

    stages {
        stage('dir') {
            steps {
                sh 'ls -la'
            }
        }
        stage('ansible') {
            steps {
                sh 'ansible --version'
            }
        }
        stage('ansible') {
            steps {
                sh 'ansible -m ping all -i .ansible/inventory.ini'
            }
        }
    }
}
