#!groovy
@Library('kubeconsult-jenkins-lib') _
import com.kubeconsult.buildlib.*

def git = com.kubeconsult.buildlib.Git(this)

pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo git.getBranchname()
            }
        }
    }
}