pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Command to build your project (e.g., using Maven or Gradle)
                // sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests...'
                // Command to run tests (e.g., using JUnit or a testing framework)
                // sh 'mvn test'
            }
            post {
                always {
                    emailext(
                        subject: "Build ${currentBuild.fullDisplayName} - Test Stage",
                        body: "Build ${currentBuild.fullDisplayName} completed. Please find attached logs for the Test stage.",
                        attachLog: true,
                        to: 'sardararkhum29@gmail.com'
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running Code Analysis...'
                // Example using SonarQube
                // sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Security Scan...'
                // Example using OWASP ZAP or other security tools
                // sh 'zap-cli quick-scan'
            }
            post {
                always {
                    emailext(
                        subject: "Build ${currentBuild.fullDisplayName} - Security Scan Stage",
                        body: "Build ${currentBuild.fullDisplayName} completed. Please find attached logs for the Security Scan stage.",
                        attachLog: true,
                        to: 'sardararkhum29@gmail.com'
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deployment command (e.g., using Docker or AWS CLI)
                // sh 'docker-compose up'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Command to deploy to production
                // sh 'docker-compose up'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}

