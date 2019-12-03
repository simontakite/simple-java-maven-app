@Library(['nets-shared-library@master'])_

pipeline {

    agent { label 'no1-stbuild-2' }
    

    // stage pipeline
    stages {

        stage('Purge modules') {
            /* when {
                anyOf {
                    branch 'dev';
                    branch 'stage';
                    buildingTag()
                }
            } */
            steps {
                script {
                    sh 'git rev-parse --short HEAD'
                }
            }
        }
        
        stage ('Test') {
            environment {
                hash = gitCommitHash()
            }
            
            steps {
                sh 'docker build -t'
            }
            post {
                success {
                    notifyBuildSuccess("https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f")
                }
                failure {
                    notifyBuildFailure("https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f")
                }
            }
        }
    }
}
