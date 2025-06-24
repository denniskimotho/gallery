pipeline {
  agent any
  
  stages {
    // stage('Clone repo'){
    //     steps{
    //         sh 'git clone https://github.com/denniskimotho/gallery.git'
    //     }
    // }
        stage('Checkout') {
            steps {
                checkout scm  // Uses SCM settings from Jenkins job
            }
        }
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
