pipeline {
 agent any
 parameters { 
       choice(name: 'SELECTION', choices: ['one', 'two', 'three'], description: '') 
 }
 environment {
  dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
 }
 stages {
  stage('Checkout') {
   steps {
   echo "Selection was ${SELECTION}"
    git url: 'https://github.com/Panther59/MammothAPI.git', branch: 'master'
   }
  }
  stage('Restore PACKAGES') {
   steps {
    bat "dotnet restore"
   }
  }
  stage('Clean') {
   steps {
    bat 'dotnet clean'
   }
  }
  stage('Build') {
   steps {
    bat 'dotnet build --configuration Release'
   }
  }
 }
}
