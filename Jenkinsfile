#!groovy
@Library('kubeconsult-jenkins-lib')
import com.kubeconsult.buildlib.*

def git = new com.kubeconsult.buildlib.Git(this)


pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Branch name') {
            steps {
                def repo = git.getBranchName()
                sh 'echo $repo'
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