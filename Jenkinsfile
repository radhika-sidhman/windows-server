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
                echo '🧱 Building .NET project...'
                bat 'dotnet build HelloApp/HelloApp.csproj'
            }
        }

        stage('Run') {
            steps {
                echo '▶️ Running application...'
                bat 'dotnet run --project HelloApp/HelloApp.csproj'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Run completed successfully!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}

