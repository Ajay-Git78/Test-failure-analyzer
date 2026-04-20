pipeline {
    agent any

    environment {
        PYTHON_EXE = "C:\\Users\\ADMIN\\AppData\\Local\\Python\\bin\\python.exe"
        SCRIPT_NAME = "hello.py"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Verify Python') {
            steps {
                echo 'Verifying Python installation...'
                bat """
                echo Python Executable:
                "%PYTHON_EXE%"

                echo Python Version:
                "%PYTHON_EXE%" --version
                """
            }
        }

        stage('Run Python Script') {
            steps {
                echo 'Executing Python script...'
                bat """
                "%PYTHON_EXE%" %SCRIPT_NAME%
                """
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished execution.'
        }
        success {
            echo '✅ Build SUCCESS'
        }
        failure {
            echo '❌ Build FAILED'
        }
    }
}
