pipeline {
  agent any
  stages {
//    stage('SonarQube Analysis') {
//      agent any
//      steps {
//        withSonarQubeEnv(installationName: 'SonarQubeServer') {
//          withMaven(maven: 'Apache Maven 3.5.4', publisherStrategy: 'EXPLICIT ') {
//            sh 'mvn sonar:sonar'
//          }

//        }

//      }
//    }
//    stage('Quality Gate') {
//      steps {
//        timeout(time: 2, unit: 'MINUTES') {
//          waitForQualityGate(abortPipeline: true)
//        }
//
//      }
//    }
    stage('Build') {
      steps {
        withMaven(maven: 'Apache Maven 3.5.4') {
          sh 'mvn clean package'
        }

      }
    }
  }
}
