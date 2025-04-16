pipeline {
    agent any

    tools {
        maven 'Maven 3.8.7'  // Must match the name configured in Jenkins
        jdk 'JDK 11'         // Optional, if JDK configured
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/SreeramPavani5/cddproject.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
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
        success {
            echo 'Maven pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
