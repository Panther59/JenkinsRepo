pipeline {
  agent {
    label 'buildagent'
  }
  environment {
    dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/Panther59/MonoRepoTrial.git', branch: 'main'
      }
    }
    stage('Build & Test') {
      matrix {
        axes {
          axis {
            name 'service'
            values 'ConsoleApp1', 'ConsoleApp2'
          }
        }
        when {
          changeset pattern: "*/$service/*"
        }
        stages {
          stage('Restore PACKAGES') {
            steps {
              dir("$service") {
                bat "dotnet restore"
              }
            }

          }
          stage('Clean') {
            steps {
              dir("$service") {
                bat "dotnet clean"
              }
            }
          }
          stage('Build') {
            steps {
              dir("$service") {
                bat "dotnet build --configuration Release"
              }
            }
          }
        }
      }
    }
  }
}
