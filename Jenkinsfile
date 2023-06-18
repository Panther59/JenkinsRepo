pipeline {
 agent any
 parameters { 
       choice(name: 'PROEJCT', choices: ['ConsoleApp1', 'ConsoleApp2'], description: 'Select project to build') 
 }
 environment {
  dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
 }
 stages {
  stage('Checkout') {
   steps {
   echo "Selection was ${PROEJCT}"
    git url: 'https://github.com/Panther59/MonoRepoTrial.git', branch: 'master'
   }
  }
  stage('Restore PACKAGES') {
   steps {
    cd "../${PROEJCT}";bat "dotnet restore"
   }
  }
  stage('Clean') {
   steps {
    cd "../${PROEJCT}";bat 'dotnet clean'
   }
  }
  stage('Build') {
   steps {
    cd "../${PROEJCT}";bat 'dotnet build --configuration Release'
   }
  }
 }
}
