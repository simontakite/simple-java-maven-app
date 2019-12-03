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
                sh "curl --request POST \
  --url https://outlook.office.com/webhook/ffaa6dbe-27b0-4e34-ad59-774fc7573c5c@df41dac6-47ab-4982-97ab-60c8af4a7dc0/IncomingWebhook/830ed6b257374b3b8d8e11714d02fa7d/008bd7a8-2a05-43ca-9969-48191de5d673 \
  --header 'Content-Type: application/json' \
  --header 'Postman-Token: 9b2dc585-48e0-43d9-836b-90ae0acf66af' \
  --header 'cache-control: no-cache' \
  --data '{\r\n  "@type": "MessageCard",\r\n  "@context": "https://schema.org/extensions",\r\n  "summary": "Issue 176715375",\r\n  "themeColor": "eb4034",\r\n  "title": "SOMETHING WENT WRONG",\r\n  "sections": [\r\n    {\r\n      "activityTitle": "**Bankart** build [#201](http://url) (FAILED) [Build logs](http://url)",\r\n      "activitySubtitle": "Finished: 9/13/2019, 11:46am triggered by **Someone**",\r\n      "activityImage": "https://cdn.pixabay.com/photo/2017/02/12/21/29/false-2061131_960_720.png",\r\n      "facts": [\r\n        {\r\n          "name": "Commit message:",\r\n          "value": "Fixed typo #3"\r\n        },\r\n        {\r\n          "name": "Branch:",\r\n          "value": "develop"\r\n        }\r\n      ]\r\n    }\r\n  ],\r\n  "potentialAction": [\r\n    {\r\n      "@type": "HttpPOST",\r\n      "name": "Bitbucket",\r\n      "target": "http://..."\r\n    },\r\n    {\r\n      "@type": "HttpPOST",\r\n      "name": "Jenkins",\r\n      "target": "http://..."\r\n    },\r\n    {\r\n      "@type": "HttpPOST",\r\n      "name": "Sonarqube",\r\n      "target": "http://..."\r\n    },\r\n    {\r\n      "@type": "HttpPOST",\r\n      "name": "Kibana",\r\n      "target": "http://..."\r\n    },\r\n    {\r\n      "@type": "OpenUri",\r\n      "name": "Rollback",\r\n      "targets": [\r\n        {\r\n          "os": "default",\r\n          "uri": "http://..."\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}'"
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
