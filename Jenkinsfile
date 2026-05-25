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
}