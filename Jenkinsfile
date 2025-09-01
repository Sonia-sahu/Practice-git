pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/your-username/SimpleCalc.git'
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

        stage('Run Calculator') {
            steps {
                sh 'mvn exec:java'
            }
        }
    }

    post {
        success {
            emailext (
                subject: "✅ Build Success: SimpleCalc",
                body: "The Jenkins build completed successfully.\nCalculator executed.",
                to: "recipient@example.com"
            )
        }
        failure {
            emailext (
                subject: "❌ Build Failed: SimpleCalc",
                body: "The Jenkins build failed. Please check the console output for details.",
                to: "recipient@example.com"
            )
        }
    }
}
