node {
        stage('Build') {
            steps {
                // Compile the Maven project
                sh 'mvn clean compile'
            }
        }
        stage('SCM') {
            checkout scm
        }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/mvn clean verify sonar:sonar -Dsonar.projectKey=devopsa4 -Dsonar.projectName='devopsa4'"
    }
  }
}

