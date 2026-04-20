pipeline {
    agent any

    environment {
        // 🔧 Update this path based on your actual Python installation
        PYTHON_HOME = "C:\\Program Files\\Python312"
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
                echo Python Path:
                where python

                echo Python Version:
                "C:\Users\ADMIN\AppData\Local\Python\bin\python.exe\\python.exe" --version
                """
            }
        }

        stage('Run Python Script') {
            steps {
                echo 'Executing Python script...'
                bat """
                "C:\Users\ADMIN\AppData\Local\Python\bin\python.exe\\python.exe" %SCRIPT_NAME%
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
