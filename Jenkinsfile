pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './app.sh'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Pretend tests passed ✅ for Christopher\'s CI/CD pipeline"'
            }
        }
    }
}
