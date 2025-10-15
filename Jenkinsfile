pipeline {
    agent any

    environment {
        // Optional: full path to dotnet if not in PATH
        DOTNET_PATH = "C:\\Program Files\\dotnet\\dotnet.exe"
    }

    stages {

        stage('Checkout') {
            steps {
                echo '📥 Checking out source code from Git...'
                git branch: 'main',
                    url: 'https://github.com/radhika-sidhman/windows-server.git',
                    credentialsId: 'windows' // replace with your Jenkins Git credential ID
            }
        }

        stage('Build') {
            steps {
                echo '🛠 Building .NET project...'
                // Build the HelloApp.csproj
                bat '"%DOTNET_PATH%" build HelloApp.csproj'
            }
        }

        stage('Run') {
            steps {
                echo '🚀 Running .NET project...'
                // Run the HelloApp.csproj
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


