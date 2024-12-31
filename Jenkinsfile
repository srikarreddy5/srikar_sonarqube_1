 pipeline{

   agent any
   stages{
stage('build'){
  steps{
    echo "im building"
  }

   }
     stage('test'){
       steps{
         echo "im testing"
       }
     }
     stage('deploy')
     {
       steps{
         echo"deploying"
       }
     }
   }
   post{
     success{
       echo "success"
     }
     failure{
       echo "failure"
     }


   }

 }
