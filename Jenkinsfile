pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/honey3031/test_framework.git'
            }
        }

        stage('Run Docker Compose') {
            steps {
                bat 'docker-compose up --build'
            }
        }

        stage('Generate Allure Report') {
            steps {
                bat 'allure generate reports/allure-results --clean -o reports/allure-report'
            }
        }

    }
}