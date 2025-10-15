pipeline {
    agent any

    environment {
        DOTNET_PATH = "C:\\Program Files\\dotnet\\dotnet.exe" // Optional: if dotnet is not in PATH
    }

    stages {

        stage('Checkout') {
            steps {
                echo '📥 Checking out source code from Git...'
                git branch: 'main',
                    url: 'https://github.com/yuvrajahire1/windows-server.git',
                    credentialsId: 'windows' // replace with your Jenkins credential ID if needed
            }
        }

        stage('Build') {
            steps {
                echo '🛠 Building .NET project...'
                // Build the project
                bat '"%DOTNET_PATH%" build HelloApp.csproj'
            }
        }

        stage('Run') {
            steps {
                echo '🚀 Running .NET project...'
                // Run the project
                bat '"%DOTNET_PATH%" run --project HelloApp.csproj'
            }
        }
    }

    post {
        success {
            echo '✅ Build and run succeeded!'
        }
        failure {
            echo '❌ Build or run failed!'
        }
        always {
            echo '🔄 Pipeline finished.'
        }
    }
}

