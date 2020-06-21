pipeline {
  agent any  
    withCredentials([[
      $class: 'AmazonWebServicesCredentialsBinding',
      credentialsId: credentialsId,
      accessKeyVariable: 'AWS_ACCESS_KEY_ID',
      secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
    ]]) {    
  stages {
          
         stage('Clone Github repository') {
           steps {
              
             checkout scm
           
            }
  
          }
    stage('Serverless build stage') {   
       steps {           
         script {      
              try {
                    ansiColor('xterm') {
                    sh 'sudo apt install -y npm' 
                    sh 'sudo npm install --unsafe-perm=true --allow-root'
                    sh 'sudo apt install  -y nodejs'			
                    sh 'sudo apt install  -y build-essential'
                    sh 'sudo npm i -g npm'
                    sh 'sudo npm install serverless -g'
                    sh 'sudo npm install -D https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
                    sh 'cloudguard -V'
                  }  
                 }
              } 
       } 
       catch (Exception e) {
         echo "Code Analysis is BLOCK and recommend not using the source code"  
       }
     }
    stage('Deploying my serverless application with CloudGuard security ') {
      steps {
         ansiColor('xterm') {
           sh 'sls deploy'
         } 
        }
      }
    }    
  }
}