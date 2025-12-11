pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Jenkins ще изтегли репото в workspace-а на job-а
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
                bat '''
dotnet test SeleniumIde.sln --configuration Debug --no-build ^
  --logger "trx;LogFileName=TestResults.trx" ^
  --logger "junit;LogFileName=TestResults.xml"
'''

                // Показваме резултатите в Tests таб-а
                junit 'SeleniumIDE/TestResults/TestResults.xml'

                // Качваме xml + trx като артефакти
                archiveArtifacts artifacts: 'SeleniumIDE/TestResults/*', fingerprint: true
            }
        }
    }
}
