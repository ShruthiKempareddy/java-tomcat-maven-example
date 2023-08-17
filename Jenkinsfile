pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/ShruthiKempareddy/java-tomcat-maven-example', branch: 'master', credentialsId: 'githubCreds')
      }
    }

    stage('build') {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: '', maven: 'Maven', mavenSettingsConfig: '', traceability: true) {
          bat 'mvn clean install'
        }
      }
    }

    stage('deploy') {
      steps {
        rtServer (
              id: 'Artifactory',
              url: 'http://localhost:8082/artifactory',
              // If you're using Credentials ID:
              credentialsId: 'admin.jfrog',
              // If Jenkins is configured to use an http proxy, you can bypass the proxy when using this Artifactory server:
              bypassProxy: true,
              // Configure the connection timeout (in seconds).
              // The default value (if not configured) is 300 seconds: 
              timeout: 300
          )
        rtUpload (
                serverId: 'Artifactory',
                spec: '''{
                      "files": [
                        {
                          "pattern": "target/java-tomcat-maven-example.war",
                          "target": "libs-release-local/"
                        }
                     ]
                }'''
            )
        }
      }
    }
}
