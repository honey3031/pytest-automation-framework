pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/honey3031/pytest-automation-framework.git'
            }
        }

        stage('Clean Docker') {
            steps {
                bat 'docker compose down'
            }
        }

        stage('Start Selenium Grid') {
            steps {
                bat 'docker compose up -d'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest -v'
            }
        }

        stage('Generate Report') {
            steps {
                bat 'python -m pytest --html=reports/report.html --self-contained-html'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html'
            bat 'docker compose down'
        }
    }
}