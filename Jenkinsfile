pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
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
deploy adapters: [tomcat9(credentialsId: '6ba870f9-82ed-4aa7-88b2-a22a5d3599aa', path: '', url: 'http://localhost:8080')], contextPath: '/exp4_5', war: '**/*.war' }
 }
 }
 }
}
