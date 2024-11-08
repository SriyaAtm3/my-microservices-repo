pipeline {
    agent any  // This specifies that the pipeline can run on any available agent (e.g., a node, container, etc.)

    tools {
        // Define the tools required for the build (e.g., Maven and JDK)
        maven 'Maven 3.6'  // Name defined in Jenkins Tool Configuration
        jdk 'JDK 11'       // Name defined in Jenkins Tool Configuration
    }

    environment {
        // Define any environment variables that can be used across the pipeline
        MAVEN_OPTS = "-Dmaven.test.failure.ignore=true"  // Optional: Ignore test failures for the build stage
    }

    stages {
        // Stage for checking out the source code from Git
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/your-repo.git'  // Replace with your repository URL
            }
        }

        // Stage for building the project using Maven
        stage('Build') {
            steps {
                script {
                    // Execute Maven to clean and package the application
                    sh 'mvn clean package -DskipTests'  // Skip tests during the build (optional)
                }
            }
        }

        // Stage for running unit tests using Maven
        stage('Test') {
            steps {
                script {
                    // Execute Maven to run unit tests
                    sh 'mvn test'
                }
            }
        }

        // Stage for deploying the application (optional, depends on your setup)
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
        // Actions that will be executed after the pipeline finishes
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Build or tests failed. Please check the logs!'
        }
    }
}
