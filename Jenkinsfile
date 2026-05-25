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
                bat 'mkdir deploy'
                bat 'copy index.html deploy'
            }
        }

    }
}