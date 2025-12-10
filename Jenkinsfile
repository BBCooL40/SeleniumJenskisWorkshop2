pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore SeleniumIde.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build SeleniumIde.sln --configuration Debug --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test SeleniumIde.sln --configuration Debug --no-build'
            }
        }
    }
}
