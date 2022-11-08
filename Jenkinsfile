pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Units') {
      parallel {
        stage('Units') {
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
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('deplyment') {
      steps {
        sh 'dotnet  publish  ~/src/web/Web.csproj eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}