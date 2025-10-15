pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/yuvrajahire1/windows-server.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                bat 'dotnet build' // or any Windows command
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying new version of HTML...'
                bat 'xcopy /Y index.html C:\\inetpub\\wwwroot\\' // example for IIS
            }
        }
    }

    post {
        failure {
            echo '❌ Build failed!'
        }
        success {
            echo '✅ Build succeeded!'
        }
    }
}
