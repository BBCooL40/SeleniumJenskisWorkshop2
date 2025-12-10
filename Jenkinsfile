node {
    stage('Restore') {
        bat 'dotnet restore SeleniumIde.sln'
    }

    stage('Build') {
        bat 'dotnet build SeleniumIde.sln --configuration Debug --no-restore'
    }

    stage('Test') {
        bat 'dotnet test SeleniumIde.sln --configuration Debug --no-build'
    }
}
