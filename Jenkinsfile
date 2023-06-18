pipeline {
 agent { label 'buildagent' }
 environment {
  dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
  projects = ['ConsoleApp1', 'ConsoleApp2']
 }                    
 
 stages {
  stage('Checkout') {
   steps {
   echo "Selection was ${PROEJCT}"
    git url: 'https://github.com/Panther59/MonoRepoTrial.git', branch: 'main'
   }
  }
  stage('Restore PACKAGES') {
   script {
    for(String proj: x) { 
     println proj 
     when { changeset "**/ConsoleApp1/*.*" }
     steps { dir("ConsoleApp1") {bat "dotnet restore"  } }   
    }
   }   
  }
  stage('Clean') {
   when { changeset "**/ConsoleApp1/*.*" }
   steps { dir("ConsoleApp1") {bat "dotnet clean"  } }   
  }
  stage('Build') {
   when { changeset "**/ConsoleApp1/*.*" }
   steps { dir("ConsoleApp1") {bat "dotnet build --configuration Release"  } }
  }
 }
}
