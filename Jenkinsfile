pipeline {
    agent any

    environment {
        PYTHON_EXE = "C:\\Users\\ADMIN\\AppData\\Local\\Python\\bin\\python.exe"
        SCRIPT_NAME = "hello.py"
    }

    triggers {
        // ⏰ Runs every 4 hours
        cron('H */4 * * *')
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Python Script') {
            steps {
                bat "\"%PYTHON_EXE%\" %SCRIPT_NAME%"
            }
        }

        stage('Print Build Info') {
            steps {
                script {
                    def currentTime = new Date().format("yyyy-MM-dd HH:mm:ss")

                    echo "=============================="
                    echo "Build Number  : ${env.BUILD_NUMBER}"
                    echo "Current Time  : ${currentTime}"
                    echo "Build Status  : SUCCESS"
                    echo "=============================="
                }
            }
        }
    }

    post {
        failure {
            script {
                def currentTime = new Date().format("yyyy-MM-dd HH:mm:ss")

                echo "=============================="
                echo "Build Number  : ${env.BUILD_NUMBER}"
                echo "Current Time  : ${currentTime}"
                echo "Build Status  : FAILURE"
                echo "=============================="
            }
        }

        always {
            echo "Pipeline finished."
        }
    }
}
