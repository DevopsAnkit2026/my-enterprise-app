pipeline {
    agent any

    tools {
        maven 'Maven-3'
        jdk 'Java-21'
    }

    environment {
        MVN_HOME = tool 'Maven-3'
    }

    stages {
        stage('Build') {
            steps {
                sh "${MVN_HOME}/bin/mvn -version"
                sh "${MVN_HOME}/bin/mvn clean package"
            }
        }
    }

    post {
        always {
            echo "Build finished!"
        }
    }
}
