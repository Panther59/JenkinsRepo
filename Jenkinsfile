pipeline {
 agent { label 'buildagent' }
 environment {
  dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
 }
 stages {
  stage('Checkout') {
   steps {
   echo "Selection was ${PROEJCT}"
    git url: 'https://github.com/Panther59/MonoRepoTrial.git', branch: 'main'
   }
  }
  stage('Restore PACKAGES') {
   when { changeset "**/ConsoleApp1/*.*" }
   steps { dir("ConsoleApp1") {bat "dotnet restore"  } }
   when { changeset "**/ConsoleApp2/*.*" }
   steps { dir("ConsoleApp2") {bat "dotnet restore"  } }
  }
  stage('Clean') {
   when { changeset "**/ConsoleApp1/*.*" }
   steps { dir("ConsoleApp1") {bat "dotnet clean"  } }
   when { changeset "**/ConsoleApp2/*.*" }
   steps { dir("ConsoleApp2") {bat "dotnet clean"  } }
  }
  stage('Build') {
   when { changeset "**/ConsoleApp1/*.*" }
   steps { dir("ConsoleApp1") {bat "dotnet build --configuration Release"  } }
   when { changeset "**/ConsoleApp2/*.*" }
   steps { dir("ConsoleApp2") {bat "dotnet build --configuration Release"  } }      
  }
 }
}
