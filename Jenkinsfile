pipeline {

    agent any

    stages {
        // build
        stage('checkout') {

            steps {
                // Run the maven build | 
                checkout(poll: false, scm: [$class: 'GitSCM', 
                	branches: [[name: '*/master']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'PathRestriction', excludedRegions: '', includedRegions: 'src/*']], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[url: "https://github.com/simontakite/simple-java-maven-app.git"]]])
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
