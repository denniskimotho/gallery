pipeline {
  agent any
  
  stages {
    stage('Setup') {
      steps {
        sh 'npm install'
      }
    }
    
    stage('Deploy') {
      steps {
        sh 'node server.js &'
      }
    }
  }
  
  triggers {
    pollSCM('* * * * *') 
 }
}