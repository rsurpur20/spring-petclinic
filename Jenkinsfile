node {
    agent { docker { image 'maven:3.9.6-eclipse-temurin-17-alpine' } }

    stage('build mvn') {
            steps {
                sh 'mvn --version'
            }
    }
    
    stage('Checkout') {
        // Checkout the code from your version control system
        git branch: 'main', url: 'https://github.com/rsurpur20/spring-petclinic'
    }

    stage('Build') {
        // Compile the Maven project
        sh 'mvn clean compile'
    }

    stage('Test') {
        // Run tests if any
        sh 'mvn test'
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
    try {
        // This block executes if the pipeline is successful
        echo 'Pipeline successfully completed!'
    } catch (Exception e) {
        // This block executes if the pipeline fails
        echo 'Pipeline failed!'
    } finally {
        // This block always executes, regardless of the pipeline outcome
        // You can do cleanup tasks here, if needed
    }
}


