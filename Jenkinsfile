pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control (e.g., Git)
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build your project (assuming it's a Maven project)
                script {
                    def mvnHome = tool 'Maven'
                    sh "${mvnHome}/bin/mvn clean install"
                }
            }
        }

        stage('Test') {
            steps {
                // Run JUnit tests
                script {
                    def mvnHome = tool 'Maven'
                    sh "${mvnHome}/bin/mvn test"
                }
            }
        }

        stage('Deploy') {
            steps {
                // Additional deployment steps if needed
                // e.g., deploying to a server or container registry
            }
        }
    }

    post {
        // Post-build actions or notifications
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
