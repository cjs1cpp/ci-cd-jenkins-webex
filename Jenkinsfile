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

        stage('Notify Webex') {
            steps {
                withCredentials([string(credentialsId: 'webex-webhook', variable: 'WEBEX_URL')]) {
                    sh '''
                      curl -X POST "$WEBEX_URL" \
                        -H "Content-Type: application/json" \
                        -d "{
                          \\"markdown\\": \\"✅ Jenkins build #$BUILD_NUMBER succeeded for repo cjs1cpp/ci-cd-jenkins-webex on branch master.\\"
                        }"
                    '''
                }
            }
        }
    }
}

