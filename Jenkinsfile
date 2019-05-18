#!groovy
@Library('kubeconsult-jenkins-lib')
import com.kubeconsult.buildlib.*

node('master') {
    stage('checkout and build') {
        def branch
        def git = new com.kubeconsult.buildlib.Git(this)
        git.getRepositoryUrl()
    }

    stage('Docker') {
        def docker = new com.kubeconsult.buildlib.Docker(this)
        docker.dockerBaseImageVersion()
    }
}