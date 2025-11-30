stage('Upload Artifact to JFrog') {
    steps {
        script {
            def server = Artifactory.server('my-artifactory')
            def uploadSpec = """{
              "files": [
                {
                  "pattern": "target/*.war",
                  "target": "libs-release-local/myenterprise-app/"
                }
              ]
            }"""

            server.upload(uploadSpec)
        }
    }
}
