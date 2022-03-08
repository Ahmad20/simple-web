pipeline { 
  
   agent any
  tools {nodejs "node"}
   stages {
   
     stage('Install Dependencies') { 
        steps { 
           bat 'npm install' 
        }
     }
     
     stage('Test') { 
        steps { 
           bat 'echo "testing application..."'
        }
      }

         stage("Deploy application") { 
         steps { 
           bat 'echo "deploying application..."'
         }

     }
  
   	}

   }
