#!groovy
@Library('kubeconsult-jenkins-lib') _
import com.kubeconsult.buildlib.*

pipeline {
    agent any
    stages {
        stage('build') {

            def git = com.kubeconsult.buildlib.Git(this)
            
            steps {
                echo git.getBranchname()
            }
        }
    }
}