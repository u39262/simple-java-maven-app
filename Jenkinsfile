pipeline {
  agent any
  stages {
    stage('SonarQube Analysis') {
      agent any
      steps {
        withSonarQubeEnv(installationName: 'SonarQubeServer') {
          withMaven(maven: 'Apache Maven 3.5.4') {
            sh 'mvn sonar:sonar'
          }

        }

      }
    }
    stage('Quality Gate') {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          waitForQualityGate(abortPipeline: true)
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
    stage('Deploy to WildFly') {
      steps {
        withMaven(maven: 'Apache Maven 3.5.4') {
          sh '''mvn wildfly:redeploy -Dwildfly.id=wildfly-dev -Dwildfly.hostname=172.20.32.247 -Dwildfly.port=9990 -Dwildfly.serverGroup=other-server-group
'''
        }

      }
    }
  }
}