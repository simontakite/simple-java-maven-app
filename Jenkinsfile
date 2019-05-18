#!groovy
@Library('kubeconsult-jenkins-lib')
import com.kubeconsult.buildlib.Git

withEnv(["branch"="master"])

node('master') {
    stage('checkout and build') {
        def branch
        def git = new com.kubeconsult.buildlib.Git(this)
        git.getBranchName()
    }
}