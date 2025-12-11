node {
    stage('Checkout') {
        // Ръчно дърпаме кода, както досега
        bat 'if not exist .git (git clone https://github.com/BBCooL40/SeleniumJenskisWorkshop2.git . ) else (git pull)'
    }

    stage('Restore') {
        bat 'dotnet restore SeleniumIde.sln'
    }

    stage('Build') {
        bat 'dotnet build SeleniumIde.sln --configuration Debug --no-restore'
    }

    stage('Test') {
        // Генерираме едновременно TRX и JUnit
        bat 'dotnet test SeleniumIde.sln --configuration Debug --no-build --logger "trx;LogFileName=TestResults.trx" --logger "junit;LogFileName=TestResults.xml"'

        // Казваме на Jenkins къде е JUnit репорта
        junit 'SeleniumIDE/TestResults/TestResults.xml'
    }
}
