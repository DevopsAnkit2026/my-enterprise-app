pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'Java21'
    }

    environment {
        ARTIFACTORY_SERVER = "jfrog-server"   // Jenkins में दिया हुआ ID
        ARTIFACT_PATH = "target/*.jar"        // WAR हुआ तो बाद में बदल देंगे
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean package -Dmaven.test.skip=true"
            }
        }

        stage('Upload Artifact to JFrog') {
            steps {
                script {

                    def server = Artifactory.server(ARTIFACTORY_SERVER)

                    def targetRepo = ""

                    // Branch → Artifactory repo mapping
                    if (env.BRANCH_NAME == "dev") {
                        targetRepo = "maven-dev-local/"
                    }
                    else if (env.BRANCH_NAME == "qa") {
                        targetRepo = "maven-qa-local/"
                    }
                    else if (env.BRANCH_NAME == "stage") {
                        targetRepo = "maven-stage-local/"
                    }
                    else if (env.BRANCH_NAME == "prod") {
                        targetRepo = "maven-prod-local/"
                    }
                    else {
                        error "Unknown branch: ${env.BRANCH_NAME}"
                    }

                    def uploadSpec = """{
                      "files": [
                        {
                          "pattern": "${ARTIFACT_PATH}",
                          "target": "${targetRepo}"
                        }
                      ]
                    }"""

                    server.upload spec: uploadSpec
                }
            }
        }
    }
}
