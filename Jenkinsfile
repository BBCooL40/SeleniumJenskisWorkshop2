pipeline {
    agent any

    stages {
        stage('DEBUG') {
            steps {
                echo '*** DEBUG: Този Jenkinsfile е от GitHub репото! ***'
                error 'Спираме нарочно, за да видим, че се изпълнява.'
            }
        }
    }
}
