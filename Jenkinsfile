#!groovy
@Library('kubeconsult-jenkins-lib')
import com.kubeconsult.buildlib.Git

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
                def git = com.kubeconsulent.buildlib.Git(this)
                git.getCommitAuthorComplete()
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