pipeline {
    agent any  // Runs on any available agent

    tools {
        maven 'Maven3'  // Ensure Maven is configured in Jenkins
    }

    environment {
        IMAGE_NAME = 'maven'
        IMAGE_TAG = 'latest'
        CONTAINER_NAME = 'maven-container'
        DOCKERFILE_PATH = './my-java-app/Dockerfile'  // Specify the Dockerfile path  
        
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'test', url: 'https://github.com/kavinkumar-007/first.git'
            }
        }

        stage('Build with Maven') {
            steps {
                dir('my-java-app') {
                sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME:$IMAGE_TAG -f $DOCKERFILE_PATH ."
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    sh """
                        docker run -d --name $CONTAINER_NAME -p 8080:8080 $IMAGE_NAME:$IMAGE_TAG
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
