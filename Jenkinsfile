pipeline {
    agent any

    tools {
        maven 'Maven-3'
        jdk 'Java-21'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -version'
                sh 'java -version'
                sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            echo "Build finished!"
        }
    }
}
