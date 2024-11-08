pipeline {
    agent any

    tools {
        maven 'Maven 3.6'
        jdk 'JDK 17'  // Make sure this matches your tool configuration in Jenkins
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

        stage('Build Service1') {
            steps {
                dir('service1') {  // Change the directory to 'service1'
                    script {
                        // Now run Maven in the 'service1' directory
                        sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        stage('Build Service2') {
            steps {
                dir('service2') {  // Change the directory to 'service2'
                    script {
                        // Now run Maven in the 'service2' directory
                        sh 'mvn clean package -DskipTests'
                    }
                }
            }
        }

        // Add additional stages for other services

    
    }
}
