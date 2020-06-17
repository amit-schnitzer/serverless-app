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
         
               
            
                sh 'apt install npm' 

                sh 'npm install serverless -g'
				sh 'curl –silent –location https://deb.nodesource.com/setup_8.x | bash	 –'
				sh 'apt-get install –yes nodejs'			
				sh ' apt-get install –yes build-essential'
				sh 'npm i -g npm'
				sh 'npm install serverless -g'
				sh 'npmconfig set prefix ‘~/.npm-global’'
				sh 'export PATH=~/.npm-global/bin:$PATH'
				sh 'npm install -g https://artifactory.app.protego.io/cloudguard-serverless-plugin.tgz'
				
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


