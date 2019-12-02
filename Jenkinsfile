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
                sh 'curl -X POST \
  https://outlook.office.com/webhook/ffaa6dbe-27b0-4e34-ad59-774fc7573c5c@df41dac6-47ab-4982-97ab-60c8af4a7dc0/IncomingWebhook/830ed6b257374b3b8d8e11714d02fa7d/008bd7a8-2a05-43ca-9969-48191de5d673 \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: f02720b6-2fbf-4ca4-9d96-da91e4784b5e' \
  -H 'cache-control: no-cache' \
  -d '{
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "success notifications",
    "themeColor": "32a852",
    "title": "SUCCESS",
    "sections": [
        {
            "activityTitle": "**Bankart** build [#201](http://url) (SUCCEEDED) [Build logs](http://url)",
            "activitySubtitle": "Finished: 9/13/2019, 11:46am triggered by **afrok**",
            "activityImage": "https://cdn.pixabay.com/photo/2017/01/13/01/22/ok-1976099_960_720.png",
            "facts": [
                {
                    "name": "Reason:",
                    "value": "Fixed typo #3"
                },
                {
                    "name": "Branch:",
                    "value": "develop"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@type": "HttpPOST",
            "name": "Bitbucket",
            "target": "http://..."
        },
        {
            "@type": "HttpPOST",
            "name": "Jenkins",
            "target": "http://..."
        },
        {
            "@type": "HttpPOST",
            "name": "Sonarqube",
            "target": "http://..."
        },
        {
            "@type": "HttpPOST",
            "name": "Kibana",
            "target": "http://..."
        },
        {
            "@type": "OpenUri",
            "name": "Release",
            "targets": [
                {
                    "os": "default",
                    "uri": "http://..."
                }
            ]
        }
    ]
}'
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
