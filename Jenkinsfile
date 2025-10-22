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
            discordSend (
                description: "Build ${currentBuild.result} - Branch: ${env.BRANCH_NAME}",
                title: "Jenkins Build",
                link: env.BUILD_URL,
                webhookUrl: 'https://discord.com/api/webhooks/1430607424624001145/knh-JtnNwCiloV8qkzQPMcaRp9-nGodL9ji5MYNgxeJhYk4ub5DzFL-GVa-q1dXP0I3e'
            )
        }
    }
}
