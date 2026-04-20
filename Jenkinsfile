pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository from GitHub...'
                // Jenkins does this automatically if configured with SCM
            }
        }
        stage('Run Python Script') {
            steps {
                echo 'Executing Python code...'
                // Use 'bat' for Windows. Ensure python is in your System PATH.
                bat "C:\Users\ADMIN\AppData\Local\Microsoft\WindowsApps\python.exe hello.py"
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished execution.'
        }
    }
}
