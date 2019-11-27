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
        
        stage("Env Variables") {
            steps {
                sh "printenv"
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
                            "summary": "success message card",
                            "themeColor": "32a852",
                            "title": "Success",
                            "sections": [
                                {
                                    "activityTitle": "**${JOB_NAME}** build [${BUILD_DISPLAY_NAME}](http://192.168.33.10:8080/job/${JOB_BASE_NAME}/${BUILD_NUMBER}/console) (FAILED) [Build logs](http://192.168.33.10:8080/job/${JOB_BASE_NAME}/${BUILD_NUMBER}/consoleText)",
                                    "activitySubtitle": "Finished: 9/13/2019, 11:46am Changes by **GIT_COMMITTER_NAME**",
                                    "activityImage": "https://cdn.pixabay.com/photo/2017/01/13/01/22/ok-1976099_960_720.png",
                                    "facts": [
                                        {
                                            "name": "Commit hash:",
                                            "value": "${GIT_COMMIT}"
                                        },
                                        {
                                            "name": "Branch:",
                                            "value": "${GIT_BRANCH}"
                                        }
                                    ]
                                }
                            ],
                            "potentialAction": [
                                {
                                    "@type": "HttpPOST",
                                    "name": "Bitbucket",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "${GIT_URL}"
                                        }
                                    ]
                                },
                                {
                                    "@type": "HttpPOST",
                                    "name": "Jenkins",
                                    "target": "${JENKINS_URL}"
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
