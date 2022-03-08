pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Ahmad20/simple-web.git'
      }
    }
        
    stage('Install dependencies') {
      steps {
        bat 'npm install'
      }
    }
    stage('Build Docker Image'){
      agent any
      steps{
        bat 'docker build -t ahmadtrg/test-nodejs-app:1.0.0 .'
      }
    }
    stage('Push Docker Image'){
      steps{
        bat "docker login -u ahmadtrg -p satuuntuksemua"
        bat 'docker push ahmadtrg/test-nodejs-app:1.0.0'
      }
    }
    stage('Run Container on Localhost'){
      steps{
        bat 'docker rm -f test-nodejs-app'
        bat 'docker run -itd --name test-nodejs-app -p 8989:80 ahmadtrg/test-nodejs-app:1.0.0'
      }
    }
  }
}
