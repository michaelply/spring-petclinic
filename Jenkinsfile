pipeline {
    agent any
    stages {
      stage("build & SonarQube analysis") {
        agent any
        steps {
            withSonarQubeEnv('mysonar') {
                sh './mvnw clean package sonar:sonar'
            }
        }
        post {
            success {
                archiveArtifacts 'target/*.jar'
            }
        }
      }
    }
}