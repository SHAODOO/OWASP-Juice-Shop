pipeline {
    agent {
        label 'windows'
    }
    stages {
        stage('Bash') {
            steps {
                bat 'ls'
            }
        }
        stage('Build') {
            steps {
                echo "Build"
            }
        }
        stage('Test'){
            steps {
                echo "Test"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy"
            }
        }
        stage('Release') {
            steps {
                echo "Release"
            }
        }
    }
}