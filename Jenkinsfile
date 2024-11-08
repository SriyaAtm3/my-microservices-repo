pipeline {
    agent any

    tools {
        maven 'Maven 3.6'
        jdk 'JDK 17'  // Ensure JDK is correctly configured
    }

    environment {
        MAVEN_OPTS = "-Dmaven.test.failure.ignore=true"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SriyaAtm3/my-microservices-repo.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    return sh(script: 'mvn clean package -DskipTests', returnStdout: true).trim()
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Example deployment logic
                    // sh 'docker build -t my-docker-username/myapp:latest .'
                    // sh 'docker push my-docker-username/myapp:latest'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed. Please check the logs!'
        }
    }
}
