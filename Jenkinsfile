@Library(['nets-jenkins-lib'])_

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
        
        stage ('Learn') {
            environment {
                hash = gitCommitHash()
            }
            
            steps {
                sh 'echo "${hash}"'
            }
        }
        post {
            success {
                notifyBuildSuccess("https://outlook.office.com/webhook/ffaa6dbe-27b0-4e34-ad59-774fc7573c5c@df41dac6-47ab-4982-97ab-60c8af4a7dc0/IncomingWebhook/830ed6b257374b3b8d8e11714d02fa7d/008bd7a8-2a05-43ca-9969-48191de5d673")
            }
        }

        /*
        stage('Lint') {

            environment {
                DATE_RUN = sh(script: 'date', , returnStdout: true).trim()
                GIT_COMMIT_HASH = sh(script: 'git rev-parse --short HEAD', , returnStdout: true).trim()
                GIT_COMMIT_AUTHOR = sh(script: "git log -1 --pretty=format:'%an'", , returnStdout: true).trim()
                GIT_COMMIT_MESSAGE = sh(returnStdout: true, script: "git log -1 --pretty=%B").trim()
                GIT_URL = sh(returnStdout: true, script: "git ls-remote --get-url").trim()
            }

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
                                            "value": "${GIT_COMMIT_MESSAGE}"
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
                                    "@type": "OpenUri",
                                    "name": "Bitbucket",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "${GIT_URL}"
                                        }
                                    ]
                                },
                                {
                                    "@type": "OpenUri",
                                    "name": "Jenkins",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "http://192.168.33.10:8080/job/${JOB_NAME}"
                                        }
                                    ]
                                },
                                {
                                    "@type": "OpenUri",
                                    "name": "SonarQube",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "http://..."
                                        }
                                    ]
                                },
                                {
                                    "@type": "OpenUri",
                                    "name": "Kibana",
                                    "targets": [
                                        {
                                            "os": "default",
                                            "uri": "http://..."
                                        }
                                    ]
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
        } */
    }
}
