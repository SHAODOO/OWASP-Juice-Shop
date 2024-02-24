pipeline {
    agent {
        label 'windows'
    }
    stages {
        stage('OWASP Dependency Check') {
            steps {
                dependencyCheck additionalArguments: '--scan \"${WORKSPACE}\"', odcInstallation: 'Dependency-Check-Installation'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
}