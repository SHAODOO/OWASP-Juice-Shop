pipeline {
    agent {
        label 'windows'
    }

    parameters {
        booleanParam(name: 'OWASP_DEPENDENCY_CHECK', defaultValue: false, description: 'Enable OWASP Dependency Check')
        booleanParam(name: 'SNYK', defaultValue: false, description: 'Enable Snyk Scan')
        booleanParam(name: 'TRIVY', defaultValue: false, description: 'Enable Trivy Scan')
    }
    
    stages {
        stage('OWASP Dependency Check') {
            when {
                expression { params.OWASP_DEPENDENCY_CHECK == true }
            }
            steps {
                dependencyCheck additionalArguments: '--scan \"${WORKSPACE}\"', odcInstallation: 'Dependency-Check-Installation'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage('Snyk') {
            when {
                expression { params.SNYK == true }
            }
            steps {
                snykSecurity failOnError: false, failOnIssues: false, snykInstallation: 'Snyk-Installation', snykTokenId: '9bd4a037-6e51-4407-a975-55d33b82deec9bd4a037-6e51-4407-a975-55d33b82deec', targetFile: '\"${WORKSPACE}\"'
            }
        }
        stage('Trivy') {
            when {
                expression { params.TRIVY == true }
            }
            steps {
                bat """
                    cd C:\\jenkins\\trivy_0.49.0_windows-64bit
                    trivy.exe
                    trivy fs --scanners vuln,secret,config,license ${WORKSPACE}
                """
            }
        }
    }
}