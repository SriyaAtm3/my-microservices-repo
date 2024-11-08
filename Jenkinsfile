pipeline {
    agent any  // This specifies that the pipeline can run on any available agent (e.g., a node, container, etc.)

    tools {
        // Define the tools required for the build (e.g., Maven and JDK)
        maven 'Maven 3.6'  // Name defined in Jenkins Tool Configuration
        jdk 'JDK 11'       // Name defined in Jenkins Tool Configuration (update to JDK 17 if needed)
    }

    environment {
        MAVEN_OPTS = "-Dmaven.test.failure.ignore=true"  // Optional: Ignore test failures for the build stage
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
                    // Wrap the logic inside a closure
                    // This ensures that the code is treated as a closure and not as an open block
                    return sh(script: 'mvn clean package -DskipTests', returnStdout: true).trim()
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run unit tests
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
