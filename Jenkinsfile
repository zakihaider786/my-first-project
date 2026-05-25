pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building website'

                // Intentionally check for a file
                bat 'type test.txt'
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
                subject: "SUCCESS: Build #${env.BUILD_NUMBER}",
                body: """
Build succeeded.

Project: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: SUCCESS
"""
            )
        }

        failure {
            mail(
                to: 'zakihaide000@gmail.com',
                subject: "FAILED: Build #${env.BUILD_NUMBER}",
                body: """
Build failed.

Project: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: FAILED

Please check Jenkins console output.
"""
            )
        }
    }
}