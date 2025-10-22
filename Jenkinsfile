pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo "Building Branch: ${env.BRANCH_NAME}"
            }
        }
        stage('Build') {
            steps {
                echo "Building Application..."
            }
        }
        stage('Test') {
            steps {
                echo "Running Tests..."
            }
        }
        stage('Fail Test') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'feature/fail-test') {
                        sh 'exit 1'
                    }
                }
            }
        }
    }
    post {
        always {
            sh """
                curl -X POST -H "Content-Type: application/json" \\
                -d '{"content": "Build ${currentBuild.result} - Branch: ${env.BRANCH_NAME} - ${env.BUILD_URL}"}' \\
                https://discord.com/api/webhooks/1430607424624001145/knh-JtnNwCiloV8qkzQPMcaRp9-nGodL9ji5MYNgxeJhYk4ub5DzFL-GVa-q1dXP0I3e
            """
        }
    }
}
