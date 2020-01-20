pipeline {

    agent any

    triggers {
        pollSCM('') // Enabling being build on Push
    }

    stages {
        // build --- |
        stage('checkout') {

            steps {
                scm {
                    git {
                        remote {
                            github('https://github.com/simontakite/simple-java-maven-app.git')
                        }
                        extensions {
                            cleanBeforeCheckout()
                            disableRemotePoll() // this is important for path restrictions to work
                            configure { git ->
                                git / 'extensions' / 'hudson.plugins.git.extensions.impl.PathRestriction' {
                                    includedRegions "src/.*"
                                    excludedRegions ""
                                }
                            }
                        }
                    }
                }
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
