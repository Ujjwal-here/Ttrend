pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh '/opt/apache-maven-3.9.10/bin clean deploy'
            }
        }
    }
}