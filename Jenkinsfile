#!groovy
@Library('kubeconsult-jenkins-lib') _
import com.kubeconsult.buildlib.*

def git = Git.getBranchName(this)

pipeline {
    agent any
    stages {
        stage('build') {

            sh '${git}'
        }
    }
}