pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7'   // Match with Maven tool name in Jenkins
        jdk 'JDK 11'          // Match with JDK tool name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SreeramPavani5/cddproject.git'
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

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

   post {
        always {
            echo 'Pipeline finished.'
            // Commented out to avoid error:
            // junit 'target/surefire-reports/*.xml'
        }
    }
}
