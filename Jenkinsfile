pipeline {
  agent any
  tools{
     {nodejs 'NodeJS'}
  }
  triggers {
        pollSCM('* * * * *')  
    }
  
  stages {
    // stage('Clone repo'){
    //     steps{
    //         sh 'git clone https://github.com/denniskimotho/gallery.git'
    //     }
    // }
        
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
  
}