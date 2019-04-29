pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      steps {
        def scannerHome = tool 'SQ scanner';
        withSonarQubeEnv('SonarQube Server') {
          sh 'sonar-scanner'
        }
      }
    }
    stage('Build') {
      steps {
        //fileExists 'pom.xml'
        withMaven(maven: 'Apache Maven 3.5.4') {
          sh 'mvn clean package'
        }
      }
    }
  }
}
