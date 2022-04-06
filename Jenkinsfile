pipeline{
  agent any  
  stages{
    
      stage("Git Checkout"){
        steps{
          sh 'git clone https://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@github.com/vali21/devopsAssessmentwJenkins'
        }
      }
      
      stage("Run an ansible playbook"){
        steps{
          dir("${env.WORKSPACE}/devopsAssessmentwJenkins"){
             sh 'chmod 400 anskey.pem'
             sh 'ansible-playbook main.yml --vault-password-file password.txt' 
          }
        }
      }
   }
}
