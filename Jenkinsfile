//@Library(['nets-shared-library@master'])_


pipeline {

    agent { label 'no1-stbuild-2' }
    // agent  any 

    /*environment {
        channel = "https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f"
    }*/
    
    stages {
        stage('build') {
            steps {
                script {
                    gitUrl = "ssh://git@bitbucket.nets.no:29481/rt247/bankart-implementation.git"
                    gitHttp = gitUrl.replace("ssh://git@bitbucket.nets.no:29481/rt247/", "")
                    echo '${gitHttp}'
                }
            }
        }
    }

        // checkout source code
        /*stage('Prepare') {
            parallel {
                stage('Create repos') {
                    steps {
                        sh 'make prepare-create-branches'
                    }
                }
                stage('Change pom versions') {
                    when {
                        anyOf {
                            branch 'cicd';
                        }
                    }
                    steps {
                        sh 'make prepare-change-pom'
                    }
                    post {
                        failure {
                            notifyBuildFailure(${env.channel})
                        }
                    }
                }
            }
        }

        // Run tests
        stage('Test') {
            parallel {
                stage('Setup jenkins') {
                    steps {
                        sh 'make test-setup-jenkins'
                    }
                }
                stage('Code analysis') {
                    when {
                        anyOf {
                            branch 'cicd';
                        }
                    }
                    steps {
                        sh 'make test-code-analysis'
                    }
                    post {
                        failure {
                            notifyBuildFailure(${env.channel})
                        }
                    }
                }
                stage('Unit test') {
                    steps {
                        sh 'make test-unit'
                    }
                    post {
                        failure {
                            notifyBuildFailure(${env.channel})
                        }
                    }
                }
            }
        }

        // Build
        stage('Build') {
            stage('Building ...') {
                steps {
                    sh 'make build'
                }
            }
            post {
                failure {
                    notifyBuildFailure(${env.channel})
                }
            }
        }

        // Release
        stage('Release') {
            parallel {
                stage('Release repo') {
                    steps {
                        sh 'make release-repos'
                    }
                }
                stage('Update Confluence') {
                    steps {
                        sh 'make release-update-confluence'
                    }
                }
                post {
                    failure {
                        notifyBuildFailure(${env.channel})
                    }
                }
            }
        }

        // Deploy
        stage('Deploy') {
            parallel {
                stage('Deploy PP') {
                    steps {
                        sh 'make deploy-pp'
                    }
                }
                stage('Deploy AT') {
                    steps {
                        sh 'make deploy-at'
                    }
                }
                stage('Deploy CT') {
                    steps {
                        sh 'make deploy-ct'
                    }
                }
                stage('Deploy Prod') {
                    steps {
                        sh 'make deploy-prod'
                    }
                }
                post {
                    failure {
                        notifyBuildFailure(${env.channel})
                    }
                    success {
                        notifyBuildSuccess($channel)
                    }
                }
            }
        }

        // Update confluence pages
        stage('Documentation') {
            stage('Update confluence') {
                steps {
                    sh 'make update-confluence'
                }
            }
            post {
                failure {
                    notifyBuildFailure(${env.channel})
                }
            }
        }

        // Create code review
        stage('Code review') {
            stage('Create reviews') {
                steps {
                    sh 'make code-review'
                }
            }
            post {
                failure {
                    notifyBuildFailure(${env.channel})
                }
            }
        }

        // Create service now change
        stage('Service Now change') {
            stage('Create service now change') {
                steps {
                    sh 'make service-now-change'
                }
            }
            post {
                failure {
                    notifyBuildFailure(${env.channel})
                }
            }
        }*/
}
