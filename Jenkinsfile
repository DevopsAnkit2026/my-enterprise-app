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
                echo "No build needed for HTML"
            }
        }

        stage('Deploy on Server') {
            when {
                branch 'dev'
            }
            steps {
                echo "Deploying to DEV Server"
                sh 'sudo cp -f index.html /var/www/html/index.html'
            }
        }

        stage('Deploy to QA') {
            when {
                branch 'qa'
            }
            steps {
                echo "Deploying to QA Server"
                sh 'sudo cp -f index.html /var/www/html/index.html'
            }
        }

        stage('Deploy to Stage') {
            when {
                branch 'stage'
            }
            steps {
                echo "Deploying to Stage Server"
                sh 'sudo cp -f index.html /var/www/html/index.html'
            }
        }

        stage('Deploy to Prod') {
            when {
                branch 'prod'
            }
            steps {
                echo "Deploying to PROD Server"
                sh 'sudo cp -f index.html /var/www/html/index.html'
            }
        }
    }
}
