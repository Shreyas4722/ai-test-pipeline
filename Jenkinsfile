pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                sh 'python3 -m pip install pytest'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m pytest'
            }
        }
    }
}
