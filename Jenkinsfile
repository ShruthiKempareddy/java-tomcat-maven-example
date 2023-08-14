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
        sh 'echo Shruthi'
        sh '${MAVEN_HOME}/bin/mvn clean install'
      }
    }

  }
}
