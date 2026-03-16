pipeline {
    agent any

    stages {

        stage('Install Python Dependencies') {
            steps {
                bat 'python -m venv venv'
                bat 'venv\\Scripts\\pip install --upgrade pip'
                bat 'venv\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Clean Docker Containers') {
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
                bat 'venv\\Scripts\\python -m pytest -v'
            }
        }

        stage('Generate Report') {
            steps {
                bat 'venv\\Scripts\\python -m pytest --html=reports/report.html --self-contained-html'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/*.html', fingerprint: true
            bat 'docker compose down'
        }
    }
}