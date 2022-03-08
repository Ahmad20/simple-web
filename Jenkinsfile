pipeline {
  agent { dockerfile true }
    
  tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Ahmad20/test-nodejs-app'
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
        bat 'docker build -t ahmadtrg/myapp:1.0.0 .'
      }
    }
    stage('Pubat Docker Image'){
      steps{
        bat "docker login -u ahmadtrg -p satuuntuksemua"
        bat 'docker pubat ahmadtrg/myapp:1.0.0'
      }
    }
    stage('Run Container on Localhost'){
      steps{
        bat 'docker rm -f myapp'
        bat 'docker run -itd --name simple-calc -p 8888:80 ahmadtrg/myapp:1.0.0'
      }
    }
  }
}
