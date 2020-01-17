pipeline {

    agent any

    stages {
        // build
        stage('checkout') {

            steps {
                // Run the maven build
                checkout(poll: false, scm: [$class: 'GitSCM', 
                	branches: [[name: '*/develop']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'PathRestriction', excludedRegions: '', includedRegions: 'src/*']], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[url: "https://bitbucket.nets.no/scm/~sktak/realtime-poc.git", credentialsId: "jenkinslib"]]])
            }
        }
        stage('list') {
            steps {
                script {
                    sh 'ls -la'
                }
            }
        }
    }
}
