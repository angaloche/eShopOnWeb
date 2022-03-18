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
        stage('unit') {
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
            sh 'dotnet tests tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'donet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}