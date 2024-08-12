pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Name should match the Maven installation in Jenkins
    }

    stages {
        stage('Build') {
            steps {
                script {
                    withMaven(maven: 'Maven 3.8.6') {
                        sh 'mvn clean install'  // Example Maven command
                    }
                }
            }
        }
    }
}
