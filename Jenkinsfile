pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/honey3031/pytest-automation-framework.git'
            }
        }

        stage('Start Selenium Grid') {
            steps {
                bat 'docker compose up -d'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest -v'
            }
        }

        stage('Generate Report') {
            steps {
                bat 'pytest --html=reports/report.html --self-contained-html'
            }
        }

    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
        }
    }
}