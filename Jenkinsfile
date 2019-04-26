node {
  stage('SCM') {
    git 'https://github.com/u39262/simple-java-maven-app'
  }
  stage('SonarQube analysis') {
    withSonarQubeEnv('SonarQube') {
      // requires SonarQube Scanner for Maven 3.2+
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
    }
  }
}
