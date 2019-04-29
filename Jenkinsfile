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
    stage('Quality Gate') {
      steps {
        timeout(time: 1, unit: 'HOURS') {
          withSonarQubeEnv('SonarQubeServer') {
            waitForQualityGate abortPipeline: true
          }
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
