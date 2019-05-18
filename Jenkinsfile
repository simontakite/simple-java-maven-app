#!groovy
//@Library('kubeconsult-jenkins-lib') _
//import com.kubeconsult.buildlib.*



pipeline {
    environment {
        def git = Git.getBranchName(this)
    }

    agent any
    stages {
        stage('build') {
            sh '${git}'

        }
    }
}