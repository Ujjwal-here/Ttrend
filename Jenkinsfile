pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh '/opt/apache-maven-3.9.10/bin/mvn clean deploy'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv(installationName: 'sonarqube-server') {
                    sh '/opt/apache-maven-3.9.10/bin/mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.11.0.3922:sonar'
                }
            }
            
        }
    }
}