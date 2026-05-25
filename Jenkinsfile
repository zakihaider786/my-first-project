pipeline {
    agent any

    stages {

        stage('Validate HTML') {
            steps {
                bat '''
                findstr /C:"</body>" index.html
                '''
            }
        }

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
                subject: "✅ SUCCESS Build #${env.BUILD_NUMBER}",
                body: "Build completed successfully."
            )
        }

        failure {
            mail(
                to: 'zakihaide000@gmail.com',
                subject: "❌ FAILED Build #${env.BUILD_NUMBER}",
                body: "Code validation failed."
            )
        }
    }
}