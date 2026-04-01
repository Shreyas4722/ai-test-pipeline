pipeline {
    agent any

    stages {

        stage('Install') {
            steps {
                sh 'python3 -m pip install pytest launchable'
            }
        }

        stage('Record Build') {
            steps {
                sh 'launchable record build --name $BUILD_NUMBER'
            }
        }

        stage('Collect Tests') {
            steps {
                sh 'python3 -m pytest --collect-only > test_list.txt'
            }
        }

        stage('AI Prioritization') {
            steps {
                sh '''
                launchable subset 
                --build $BUILD_NUMBER 
                --target 50% 
                test_list.txt > prioritized_tests.txt
                '''
            }
        }

        stage('Run Selected Tests') {
            steps {
                sh 'python3 -m pytest -k "$(cat prioritized_tests.txt)"'
            }
        }

        stage('Record Results') {
            steps {
                sh 'launchable record tests pytest'
            }
        }
    }
}
