pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aratij56/flask.git'
            }
        }

        stage('Setup Python & Install Dependencies') {
            steps {
                sh '''
                python3 -m pip install --upgrade pip
                pip3 install -r examples/celery/requirements.txt
                pip3 install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_ci.py'
            }
        }

        stage('Dummy Step') {
            steps {
                sh 'echo "CI is running successfully"'
            }
        }
    }
}