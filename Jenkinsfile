pipeline {
    agent any

    environment {
        GIT_CRED = 'github_pat'
        REPO_URL = 'https://github.com/DevopsAnkit2026/my-enterprise-app.git'
    }

    stages {
        stage('DEV Build & Test') {
            when { branch 'dev' }
            steps {
                echo "Running DEV pipeline..."
                sh 'ls -l'
            }
        }

        stage('QA Deploy') {
            when { branch 'qa' }
            steps {
                echo "QA deployment..."
            }
        }

        stage('STAGE Deploy') {
            when { branch 'stage' }
            steps {
                echo "STAGE deployment..."
            }
        }

        stage('PROD Deploy') {
            when { branch 'prod' }
            steps {
                echo "Production deployment..."
            }
        }
    }

    post {
        success { echo "Pipeline Success ✔️" }
        failure { echo "Pipeline Failed ❌" }
    }
}
