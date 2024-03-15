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
deploy adapters: [tomcat9(credentialsId: '7cda37a0-e46e-4ed5-a2a3-d4f682113dcb', path: '/manager/text', url: 'http://20.244.45.6:9090')], contextPath: '/cicd-web-app', war: '**/*.war'
 }
 }
 }
 }
}
