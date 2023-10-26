pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''dotnet build C:\\\\ProgramData\\\\Jenkins\\\\.jenkins\\\\workspace\\\\eShopOnWeb_build_jenkins\\\\eShopOnWeb.sln
'''
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
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