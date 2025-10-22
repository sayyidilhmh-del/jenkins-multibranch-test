pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo "Building Branch: ${env.BRANCH_NAME}"
                sh 'git branch'
            }
        }
        stage('Build') {
            steps {
                echo "Building Application..."
                sh 'echo "Simulasi build process"'
            }
        }
        stage('Test') {
            steps {
                echo "Running Tests..."
                sh 'echo "Simulasi running tests"'
            }
        }
    }
    post {
        always {
            echo "Pipeline selesai: ${currentBuild.result}"
        }
    }
}
