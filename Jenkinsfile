pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Set up Python & Install Dependencies') {
            steps {
                sh '''
                    python3 --version
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt || pip install pytest
                '''
            }
        }

        stage('Run Pytest') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }
    }
}
