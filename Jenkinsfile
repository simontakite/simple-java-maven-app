pipeline {

    agent any

    stages {
        // build
        stage('checkout') {

            steps {
                // Run the maven build | 
                /* checkout(poll: false, scm: [$class: 'GitSCM', 
                	branches: [[name: 'master']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'PathRestriction', excludedRegions: '', includedRegions: 'src/*']], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[url: "https://github.com/simontakite/simple-java-maven-app.git"]]]) */
                scm {
                    git {
                        remote {
                            url 'https://github.com/simontakite/simple-java-maven-app.git'
                        }

                        branch '*/master'

                        // Add extensions 'SparseCheckoutPaths' and 'PathRestriction'
                        def nodeBuilder = NodeBuilder.newInstance()

                        def pathRestrictions = nodeBuilder.createNode('hudson.plugins.git.extensions.impl.PathRestriction')
                        pathRestrictions.appendNode('includedRegions', 'src/.*')
                        extensions {
                            extensions << pathRestrictions
                        }
                    }
                }
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
