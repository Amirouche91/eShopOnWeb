pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet Test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test Tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet/'
      }
    }

  }
}