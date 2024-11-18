pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                echo 'Restoring dependencies...'
                bat 'dotnet restore' // Use `bat` instead of `sh` for Windows compatibility
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
