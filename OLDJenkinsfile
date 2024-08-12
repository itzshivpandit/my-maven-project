pipeline {
    agent any

    //tools {
      //  maven 'Maven 3.8.7'  // Replace 'Maven' with the exact name of your Maven installation in Jenkins
    //}

    //environment {
      //  MAVEN_HOME = tool 'Maven 3.8.7'  // Adjust if your Maven tool is named differently
    //}

    stages {
        stage('SCM Checkout') {
            steps {
                // Checkout code from GitHub
                git branch: 'main', credentialsId: 'X-X-X-X_X___XX_XX__X_X_X_X_XX__X', url: 'https://github.com/itzshivpandit/my-maven-project.git'
                script {
                    tag = sh(script: "git log -n 1 --pretty=format:'%H'", returnStdout: true).trim()
                    echo "Checked out commit: ${tag}"
                }
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml' // Collect test reports
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }

        success {
            // Actions to perform if the pipeline succeeds
            echo 'Pipeline succeeded!'
        }

        failure {
            // Actions to perform if the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
