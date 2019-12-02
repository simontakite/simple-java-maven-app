@Library(['nets-shared-library@master'])_

pipeline {

    agent any
    

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
                sh 'curl --request POST \
  --url https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f \
  --header 'Content-Type: application/json' \
  --header 'Postman-Token: 4023980e-b631-4a21-bc37-b4209df22e5f' \
  --header 'cache-control: no-cache' \
  --data '{\n    "@type": "MessageCard",\n    "@context": "https://schema.org/extensions",\n    "summary": "success notifications",\n    "themeColor": "32a852",\n    "title": "SUCCESS",\n    "sections": [\n        {\n            "activityTitle": "**Bankart** build [#201](http://url) (SUCCEEDED) [Build logs](http://url)",\n            "activitySubtitle": "Finished: 9/13/2019, 11:46am triggered by **afrok**",\n            "activityImage": "https://cdn.pixabay.com/photo/2017/01/13/01/22/ok-1976099_960_720.png",\n            "facts": [\n                {\n                    "name": "Reason:",\n                    "value": "Fixed typo #3"\n                },\n                {\n                    "name": "Branch:",\n                    "value": "develop"\n                }\n            ]\n        }\n    ],\n    "potentialAction": [\n        {\n            "@type": "HttpPOST",\n            "name": "Bitbucket",\n            "target": "http://..."\n        },\n        {\n            "@type": "HttpPOST",\n            "name": "Jenkins",\n            "target": "http://..."\n        },\n        {\n            "@type": "HttpPOST",\n            "name": "Sonarqube",\n            "target": "http://..."\n        },\n        {\n            "@type": "HttpPOST",\n            "name": "Kibana",\n            "target": "http://..."\n        },\n        {\n            "@type": "OpenUri",\n            "name": "Release",\n            "targets": [\n                {\n                    "os": "default",\n                    "uri": "http://..."\n                }\n            ]\n        }\n    ]\n}''
            }
            /*post {
                success {
                    notifyBuildSuccess("https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f")
                }
                failure {
                    notifyBuildFailure("https://outlook.office.com/webhook/1798ddcb-c988-4a06-8f8c-ce3148559169@79dc228f-c8f2-4016-8bf0-b990b6c72e98/IncomingWebhook/e9c54d644ca948bc96583b4f83f697fe/961972c6-bcc2-4d50-8163-666c06d3a57f")
                }
            } */
        }
    }
}
