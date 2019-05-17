// pipeline {
//     agent {
//         docker 'maven:alpine'
//     }
//     stages {
//         stage('Test') {
//             steps {
//                 sh 'mvn test'
//             }
//         }
//         stage('Package') {
//             steps {
//                 sh 'mvn package'
//             }
//         }
//         stage('Quality Analysis') {
//             steps{
//                 sh 'mvn sonar:sonar \
//                 -Dsonar.projectKey=simple-maven-app \
//                 -Dsonar.host.url=http://192.168.99.102:32382/sonar \
//                 -Dsonar.login=7f7b85e4384f58e7e173fafec82a02e70f31f3f5 \
//                 -Dsonar.projectVersion=$BUILD_TAG \
//                 -Dsonar.analysis.buildNumber=$BUILD_NUMBER \
//                 -Dsonar.analysis.pipeline=$BUILD_NUMBER \
//                 -Dsonar.analysis.sha1=$GIT_COMMIT \
//                 -Dsonar.analysis.repository=$GIT_URL'
//             }
//         }
//     }
// }

#!groovy

node('docker') {

  @Library('github.com/simontakite/kubeconsult-jenkins-lib@b1bbcca')
  import com.kubeconsult.buildlib.*

  Maven mvn = new MavenInDocker(this, "3.5.0-jdk-8")

  stage('Build') {
    mvn 'clean install'
  }
}
