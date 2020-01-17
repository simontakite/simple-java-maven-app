pipeline {

    agent any

    stages {
        // build
        stage('checkout') {

            steps {
                // Run the maven build |
                scm {
                    git {
                        remote {
                            github('https://github.com/simontakite/simple-java-maven-app.git')
                        }
                        branch('*/masters')
                        configure { node ->
                            node / 'extensions' << 'hudson.plugins.git.extensions.impl.PathRestriction' {
                                includedRegions 'src/.*'
                                excludedRegions ''
                            }
                        }
                        extensions {
                            cleanAfterCheckout()
                            cleanBeforeCheckout()
                            cloneOptions {
                                shallow(true)
                            }
                            wipeOutWorkspace()
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
