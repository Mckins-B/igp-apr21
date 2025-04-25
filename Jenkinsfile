pipeline {
    agent any  
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

    }
}
