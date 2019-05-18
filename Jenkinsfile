#!groovy
//@Library('kubeconsult-jenkins-lib') _
//import com.kubeconsult.buildlib.*



pipeline {
    agent {
        any
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo hello'
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
            }
        }
        stage('Deliver') {
            steps {
                sh 'echo deliver'
            }
        }
    }
}