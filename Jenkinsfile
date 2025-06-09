pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    stages {
        stage('Build') {
            steps {
                echo '-------------------- build started --------------------'
                sh '/opt/apache-maven-3.9.10/bin/mvn clean deploy -Dmaven.test.skip=true'
                echo '-------------------- build completed --------------------'
            }
        }
        stage("Test") {
            steps {
                echo '-------------------- test started --------------------'
                sh '/opt/apache-maven-3.9.10/bin/mvn surefire-report:report'
                echo '-------------------- test completed --------------------'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv(installationName: 'sonarqube-server') {
                    sh '/opt/apache-maven-3.9.10/bin/mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.11.0.3922:sonar -Dsonar.projectKey=sonar-chiku_ttrend -Dsonar.organization=sonar-chiku -Dsonar.projectName=ttrend -Dsonar.sources=src/main/java -Dsonar.tests=src/test/java -Dsonar.language=java -Dsonar.sourceEncoding=UTF-8 -Dsonar.java.binaries=target/classes -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml -Dsonar.verbose=true'
                }
            }
            
        }
    }
}