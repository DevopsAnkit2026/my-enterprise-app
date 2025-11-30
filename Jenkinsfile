pipeline {
    agent any

    environment {
        JFROG_SERVER = 'my-artifactory'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Upload to JFrog') {
            steps {
                script {
                    def server = Artifactory.server(env.JFROG_SERVER)

                    def uploadSpec = """{
                      "files": [
                        {
                          "pattern": "target/*.war",
                          "target": "libs-release-local/myapp/"
                        }
                      ]
                    }"""

                    server.upload(uploadSpec)
                }
            }
        }
    }
}
