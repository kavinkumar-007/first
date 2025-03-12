pipeline {
    agent any

    tools {
        maven 'Maven_3.8'  // Ensure Jenkins has this tool configured
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'maven', url: 'https://github.com/kavinkumar-007/first.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy step (modify as needed)"
            }
        }
    }
}
