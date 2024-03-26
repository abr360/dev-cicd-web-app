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
deploy adapters: [tomcat9(credentialsId: '53052416-144b-4106-9e1c-44ba72f817eb', path: '', url: 'http://localhost:8080/')], contextPath: '/ci-cd', war: '**/*.war'
 }
 }
 }
}
