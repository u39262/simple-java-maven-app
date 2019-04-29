pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv(installationName: 'SQ scanner') {
          sh 'sonar-scanner'
        }

      }
    }
    stage('Build') {
      steps {
        withMaven(maven: 'Apache Maven 3.5.4') {
          sh 'mvn clean package'
        }

      }
    }
  }
}