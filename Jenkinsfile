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
        withMaven {
          sh "mvn clean verify"
        }
      }
    }

  }
}
