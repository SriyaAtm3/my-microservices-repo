pipeline {
    agent any

    tools {
        maven 'Maven 3.6'
        jdk 'JDK 17'  // Ensure JDK is properly configured in Jenkins tool
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
                    // Explicit closure to avoid ambiguity
                    // Wrap this in a closure (parameterless)
                    sh 'mvn clean package -DskipTests' 
                    // Explicitly invoke the closure
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run unit tests in the script block
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deployment logic, for example, Docker build and push
                    sh 'docker build -t my-docker-username/myapp:latest .'
                    sh 'docker push my-docker-username/myapp:latest'
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
