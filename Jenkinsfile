stages {

    stage('Clone Code') {
        steps {
            git 'https://github.com/your-username/your-repo.git'
        }
    }

    stage('Install Dependencies') {
        steps {
            sh 'pip install pytest launchable'
        }
    }

    stage('Collect Tests') {
        steps {
            sh 'pytest --collect-only > test_list.txt'
        }
    }

    stage('Run Tests (Basic)') {
        steps {
            sh 'pytest'
        }
    }
}
