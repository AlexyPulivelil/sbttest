// @Library('sds-common') _

// def awsS3path = "s3://pai-management-artifactory/artifacts/dev/son-sds-spark-core"
// def SparkRepoName = "son-sds-spark-core-"
// def sbt16Cmd = "/usr/bin/sbt"

pipeline {

    agent any

    environment {

        JFROG_CLI_BUILD_NAME = "${env.JOB_NAME}"

        JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"

    }
    stages {

       stage('upload') {
           steps {
                echo "${env.buildNumber}"
                echo "${env.BUILD_NUMBER}"
              //script { 
                //JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"
                //  def server = Artifactory.server 'pe-jfrog'
                //  def uploadSpec = """{
                //     "files": [{
                //        "pattern": "target/scala-2.12/*.jar",
                //        "target": "sds-pe-core"
                //     }]
                //  }"""

                //  server.upload(uploadSpec) 
                rtUpload (
                    serverId: "techino",
                    //buildNumber: "${env.BUILD_NUMBER}",
                    spec: """{
                        "files": [
                            {
                            "pattern": "target/scala-3.2.1/*.jar",
                            "target": "artifacttest" 
                            }
                        ]
                    }""",
                    buildName: 'artifacttest',
                    buildNumber: '10',
                )
               //}
            }
        }

        stage('Publish build info'){
            steps {
                rtPublishBuildInfo(
                    serverId: "techino",
                    buildName: "artifacttest",
                    buildNumber: "10"
                    
                )
            }
        }

    }

}