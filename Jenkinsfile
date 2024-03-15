pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 sh "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '46865a36-1b9d-4162-8ad0-c909db5bc068', path: ' \'/manager/text', url: 'http://20.244.45.6:9090/')], contextPath: '/dev-cicd-web-app', war: '**/*.war'
 }
 }
 }
 }
}
