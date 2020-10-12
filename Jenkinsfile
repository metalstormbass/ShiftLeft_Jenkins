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
             script {      
              try {
                    sh 'chmod +x shiftleft' 
                    sh './shiftleft iac-assessment -r 201981 -p ./'
              }    catch (Exception e) {
    
                 echo "Request for Approval"  
                  }
            }
      }
    }
  stage('Code approval request') {
     
           steps {
             script {
               def userInput = input(id: 'confirm', message: 'This code contained a rule violation. Would you still like to deploy it?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Approve Code to Proceed', name: 'approve'] ])
              }
            }
          }
  }
}
