pipeline {
    agent any  
    environment {
        DOCKER_IMAGE = "markinsb/abcapp"
        WORK_DIR = "/var/lib/jenkins/workspace/pipeline"
    }
    stages {
        stage('Code Checkout') {
            steps {
                // Checkout code
                git  branch: 'main', url: 'https://github.com/Mckins-B/igp-apr21.git'
            }
        }

        stage('Code Compile') {
            steps {
                // Compile the code using Maven
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                sh 'mvn test'
            }
        }

        stage('Build') {
            steps {
                // Package the application using Maven
                sh 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Copy the WAR file and build the Docker image
                sh 'cp ${WORK_DIR}/target/ABCtechnologies-1.0.war abc_tech.war'
                sh 'docker build -t ${DOCKER_IMAGE}:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push Docker image to DockerHub
                withDockerRegistry([credentialsId: "docker-id", url: ""]) {
                    sh 'docker push ${DOCKER_IMAGE}:latest'
                }
            }
        }

    }
}
