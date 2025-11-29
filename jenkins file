pipeline {
    agent any

    tools {
        maven 'Maven-3'        // Jenkins → Global Tool Config → Maven name
        jdk 'Java-21'          // Jenkins → Global Tool Config → JDK name
    }

    stages {
        
        stage('Check Tools Version') {
            steps {
                sh '''
                    echo "=== JAVA VERSION ==="
                    java -version

                    echo "=== MAVEN VERSION ==="
                    mvn -version
                '''
            }
        }

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                sh '''
                    echo "Starting Maven Build..."
                    mvn clean package
                '''
            }
        }
    }
}
