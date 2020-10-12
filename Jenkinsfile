pipeline {
      agent any
      environment {
           CHKP_CLOUDGUARD_ID = credentials("CHKP_CLOUDGUARD_ID")
           CHKP_CLOUDGUARD_SECRET = credentials("CHKP_CLOUDGUARD_SECRET")
        }
        
  stages {
          
         stage('Clone Github repository') {
            
    
           steps {
              
             checkout scm
           
             }
  
          }
  stage('Terraform config policy Scan') {    
           
            steps {
                    sh 'chmod +x shiftleft' 
                    sh './shiftleft iac-assessment -r 201981 -p ./'
                    
              }
            }
    }
}
