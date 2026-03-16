pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Docker Compose') {
            steps {
                bat 'docker-compose up --build'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Generate Allure Report') {
            steps {
                bat 'pytest --alluredir=reports/allure-results'
            }
        }

    }
}