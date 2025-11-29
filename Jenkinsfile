pipeline {
    agent any
    
    tools {
        maven 'maven3'      // Jenkins → Global Tool Config me jo name diya hai
        jdk 'jdk-21'        // Jenkins me JDK ka name
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mvn clean package -DskipTests
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo "Build completed."
        }
    }
}
