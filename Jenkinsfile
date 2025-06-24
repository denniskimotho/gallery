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

   post {
        
        failure {
            slackSend(
                channel: '#yourname_ip1',
                message: ":x: FAILURE - Build ${BUILD_NUMBER}\n" +
                         "Build Log:  console",
                color: 'danger'
            )
            emailext body: 'Tests failed in build ${BUILD_NUMBER}', 
                     subject: 'Test Failure', 
                     to: 'denniskimotho222@gmail.com'
        }
    }
  
}
