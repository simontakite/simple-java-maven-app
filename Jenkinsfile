pipeline {

    agent any

    triggers {
        pollSCM('') // Enabling being build on Push
    }

    stages {
        // build --- |
        stage('checkout') {

            steps {
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/master']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'DisableRemotePoll'], [$class: 'PathRestriction', excludedRegions: '', includedRegions: 'src/.*']], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[credentialsId: 'jenkinsgithub', url: 'https://github.com/simontakite/simple-java-maven-app.git']]])
            }
        }
        stage('list') {
            steps {
                script {
                    sh 'ls -l'
                }
            }
        }
    }
}
