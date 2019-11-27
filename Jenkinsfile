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
                sh "echo node_modules"
            }
        }

        stage('Lint') {

            /* agent {
                docker "circleci/node:lts-browsers-legacy"
            }

            when {
                anyOf {
                    branch 'dev';
                    branch 'stage';
                    buildingTag()
                }
            } */
            steps {
                echo "Lint"
            }
            post {
                success {
                    script {
                        def payload = """
                        {
                            "@type": "MessageCard",
                            "@context": "https://schema.org/extensions",
                            "summary": "Issue 176715375",
                            "themeColor": "eb4034",
                            "title": "FAIL",
                            "sections": [
                                {
                                    "activityTitle": "**Bankart** build [#201](http://url) (FAILED) [Build logs](http://url)",
                                    "activitySubtitle": "Finished: 9/13/2019, 11:46am Changes by **Someone**",
                                    "activityImage": "https://cdn.pixabay.com/photo/2017/02/12/21/29/false-2061131_960_720.png",
                                    "facts": [
                                        {
                                            "name": "Commit message:",
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
                                    "name": "Rollback",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "http://..."
                                        }
                                    ]
                                }
                            ]
                        }
                        """
                        httpRequest httpMode: 'POST',
                            acceptType: 'APPLICATION_JSON',
                            contentType: 'APPLICATION_JSON',
                            url: "https://outlook.office.com/webhook/ffaa6dbe-27b0-4e34-ad59-774fc7573c5c@df41dac6-47ab-4982-97ab-60c8af4a7dc0/IncomingWebhook/830ed6b257374b3b8d8e11714d02fa7d/008bd7a8-2a05-43ca-9969-48191de5d673",
                            requestBody: payload
                    }
                }
            }
        }
    }
}
