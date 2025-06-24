pipeline {
  agent any
  tools{
     nodejs 'NodeJS'
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
    stage('Test Git') {
    steps {
        sh 'git --version'
    }
}
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
    
    stage('Deploy to server') {
      steps {
        sh 'node server.js &'
      }
    }
  }
  
}
