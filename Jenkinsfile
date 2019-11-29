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
            } */
            environment {
                DATE_RUN = sh(script: 'date', , returnStdout: true).trim()
                GIT_COMMIT_HASH = sh(script: 'git rev-parse --short HEAD', , returnStdout: true).trim()
                GIT_COMMIT_AUTHOR = sh(script: 'git show | grep Author | cut -d ' ' -f2- | rev | cut -d ' ' -f2- | rev', , returnStdout: true).trim()
            }
            /*
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
                                    "activityTitle": "**${JOB_NAME}** build [${BUILD_DISPLAY_NAME}](http://vm-stbuild-5:9998/job/${JOB_BASE_NAME}/${BUILD_NUMBER}/console) (SUCCEEDED) [Build logs](http://vm-stbuild-5:9998/job/${JOB_BASE_NAME}/${BUILD_NUMBER}/consoleText)",
                                    "activitySubtitle": "Finished: ${DATE_RUN} Changes by **${GIT_COMMIT_AUTHOR}**",
                                    "activityImage": "https://cdn.pixabay.com/photo/2017/01/13/01/22/ok-1976099_960_720.png",
                                    "facts": [
                                        {
                                            "name": "Hash:",
                                            "value": "${GIT_COMMIT_HASH}"
                                        },
                                        {
                                            "name": "Message:",
                                            "value": "${STAGE_NAME}"
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
