#!groovy
@Library('kubeconsult-jenkins-lib') _
import com.kubeconsult.buildlib.*

pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                def git = com.kubeconsult.buildlib.Git(this)
                echo git.getBranchname()
            }
        }
    }
}