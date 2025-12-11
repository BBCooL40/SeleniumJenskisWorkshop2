pipeline {
    agent any

    stages {
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
            }
        }
    }

    post {
        always {
            // JUnit репорт за Tests таба
            junit 'SeleniumIDE/TestResults/TestResults.xml'

            // TRX + XML като артефакти
            archiveArtifacts artifacts: 'SeleniumIDE/TestResults/*', fingerprint: true, allowEmptyArchive: true
        }
    }
}
