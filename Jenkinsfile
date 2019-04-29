pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        fileExists 'pom.xml'
        sh 'mvn clean package'
      }
    }
  }
}