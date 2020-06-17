pipeline {
      agent any      
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
                sh 'sudo apt install -y npm' 
				        sh 'sudo apt-get install –yes nodejs'			
                sh 'sudo apt-get install –yes build-essential'
                sh 'sudo npm i -g npm'
                sh 'sudo npm install serverless -g'
                sh 'sudo npmconfig set prefix ‘~/.npm-global’'
                sh 'export PATH=~/.npm-global/bin:$PATH'
                sh 'sudo npm install -g https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
				
               } catch (Exception e) {
    
                 echo "Code Analysis is BLOCK and recommend not using the source code"  
                  }
              }
            }
         }
           
           
          stage('Deploying my serverless application with CloudGuard security ') {
             
            steps {

              sh 'sls deploy'
           
              
             } 
           }
        
  } 
}

