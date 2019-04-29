pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      steps {
        withMaven(maven: 'Apache Maven 3.5.4') {
          sh "mvn sonar:sonar"
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
