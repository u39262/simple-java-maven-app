pipeline {
	agent {
		docker {
			image 'maven'
			args '-v /root/.m2:/root/.m2'
		}
	}
	stages {
		stage('SonarQube analysis') {
    			withSonarQubeEnv('My SonarQube Server') {
     				sh 'mvn clean package sonar:sonar'
    			} // SonarQube taskId is automatically attached to the pipeline context
 		 }
		stage("Quality Gate"){
  			timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
   				def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
    				if (qg.status != 'OK') {
      					error "Pipeline aborted due to quality gate failure: ${qg.status}"
    				}
  			}
		}
//		stage('Build') {
//			steps {
//				sh 'mvn -B -DskipTests clean package'
//			}
//		}
	}
}
