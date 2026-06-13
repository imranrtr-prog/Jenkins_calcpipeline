// tutorials to create a jenkins pipeline for a python project
pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/imranrtr-prog/Jenkins_calcpipeline.git'
            }
        }

        stage('Check Python Version') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Setup Environment & Dependencies') {
            steps {
                // Create environment and upgrade pip/install dependencies in one go
                sh '''
                    python3 -m venv venv
                    ./venv/bin/pip install --upgrade pip
                    ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Test Cases') {
            steps {
                // Call pytest directly from the virtual environment bin folder
                sh './venv/bin/pytest test_calculator.py'
            }
        }
    }
    
    post {
        success {
            echo 'Calculator Pipeline completed successfully!'
        }
        failure {
            echo 'Calculator Pipeline failed!'
        }
    }   
}
