#!groovy
@Library('kubeconsult-jenkins-lib') _
import com.kubeconsult.buildlib.*


pipeline {
    agent any
    stages {
        stage('build') {
            def git = Git.getBranchName(this)
            sh '${git}'
        }
    }
}