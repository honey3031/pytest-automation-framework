pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Run Docker Compose') {
            steps {
                bat 'docker-compose up --build'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest'
            }
        }

        stage('Generate Allure Report') {
            steps {
                bat 'python -m pytest --alluredir=reports/allure-results'
            }
        }

    }
}