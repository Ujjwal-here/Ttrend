pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    environment {
        PATH+MAVEN = '/opt/apache-maven-3.9.10/bin'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}