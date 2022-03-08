pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Ahmad20/test-nodejs-app'
      }
    }
        
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }
     
    //stage('Test') {
    //  steps {
    //    sh 'npm run'
    //     sh 'npm test server.js'
   //   }
   // }  
    stage('Build Docker Image'){
      steps{
        sh 'docker build -t ahmadtrg/myapp:1.0.0 .'
      }
    }
    stage('Push Docker Image'){
      steps{
        sh "docker login -u ahmadtrg -p satuuntuksemua"
        sh 'docker push ahmadtrg/myapp:1.0.0'
      }
    }
    stage('Run Container on Localhost'){
      steps{
        sh 'docker rm -f myapp'
        sh 'docker run -itd --name simple-calc -p 8888:80 ahmadtrg/myapp:1.0.0'
      }
    }
  }
}
