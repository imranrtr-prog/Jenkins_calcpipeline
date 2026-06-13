// tutorials to create a jenkins pipeline for a python project
pipeline {
    agent any
    
    stages {
        stage('clone repository') { // Open stage brace
            steps {
                git branch: 'main', url: 'https://github.com/imranrtr-prog/Jenkins_calcpipeline.git'
            }
        } // Close stage brace

        stage('check python version') { // Open stage brace
            steps {
                sh 'python3 --version'
            }
        } // Close stage brace

        stage('Create virtual environment') { // Open stage brace
            steps {
                sh 'python3 -m venv venv'
            }
        } // Close stage brace

        stage('install dependencies') { // Open stage brace
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        } // Close stage brace

        stage(' Run test cases') { // Open stage brace
            steps {
                sh '''
                    . venv/bin/activate
                    pytest test_calculator.py
                '''
            }
        } // Close stage brace
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

