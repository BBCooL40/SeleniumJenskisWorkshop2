node {
    stage('Checkout') {
        // Ръчно си дърпаме кода с git CLI, без Jenkins плъгини
        bat '''
if not exist .git (
  git clone https://github.com/BBCooL40/SeleniumJenskisWorkshop2.git .
) else (
  git pull
)

dir
'''
    }

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
