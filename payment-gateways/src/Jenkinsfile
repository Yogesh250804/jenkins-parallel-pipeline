pipeline {
    agent any

    stages {
        stage('Parallel Build') {
            parallel {
                stage('Build feature-login') {
                    when { branch 'feature-login' }
                    steps {
                        echo "Building Application for feature-login branch"
                        sh 'echo Running build process for feature-login'
                    }
                }

                stage('Build feature-payment') {
                    when { branch 'feature-payment' }
                    steps {
                        echo "Building Application for feature-payment branch"
                        sh 'echo Running build process for feature-payment'
                    }
                }
            }
        }

        stage('Post Build') {
            steps {
                echo "Post build stage executed for branch: ${env.BRANCH_NAME}"
            }
        }
    }

    post {
        success {
            echo "✅ Build successful for branch: ${env.BRANCH_NAME}"
        }
        failure {
            echo "❌ Build failed for branch: ${env.BRANCH_NAME}"
        }
    }
}
