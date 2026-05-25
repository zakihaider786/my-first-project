pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building website'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                if exist deploy rmdir /s /q deploy
                mkdir deploy
                copy index.html deploy
                '''
            }
        }
    }

    post {

        success {
            mail(
                to: 'zakihaide000@gmail.com',
                subject: "✅ SUCCESS: Build #${env.BUILD_NUMBER}",
                body: """
Build completed successfully.

Project: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: SUCCESS

GitHub push detected and deployment completed successfully.
"""
            )
        }

        failure {
            mail(
                to: 'zakihaide000@gmail.com',
                subject: "❌ FAILED: Build #${env.BUILD_NUMBER}",
                body: """
Build failed.

Project: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: FAILED

Please check Jenkins console output for error details:
${env.BUILD_URL}console
"""
            )
        }
    }
}