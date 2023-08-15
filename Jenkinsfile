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
          sh 'mvn clean install'
        }
      }
    }

  }
}
