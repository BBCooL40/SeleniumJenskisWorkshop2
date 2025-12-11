pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                bat 'if not exist .git (git clone https://github.com/BBCooL40/SeleniumJenskisWorkshop2.git . ) else (git pull)'
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
                bat 'dotnet test SeleniumIde.sln --configuration Debug --no-build --logger "trx;LogFileName=TestResults.trx" --logger "junit;LogFileName=TestResults.xml"'

                // показваме резултатите в Tests таб-а
                junit 'SeleniumIDE/TestResults/TestResults.xml'

                // качваме файловете като артефакти
                archiveArtifacts artifacts: 'SeleniumIDE/TestResults/*', fingerprint: true
            }
        }
    }
}
