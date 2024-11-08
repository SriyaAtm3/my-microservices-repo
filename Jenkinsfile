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
                    // Explicit closure to avoid Groovy compilation error
                    sh 'mvn clean package -DskipTests'  // Skip tests during the build (optional)
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Execute Maven to run unit tests
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Example deployment step, e.g., push to Docker Hub
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
