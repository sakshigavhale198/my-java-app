pipeline {
    agent any

    tools {
        // Must match the names you configured in Jenkins -> Manage Jenkins -> Tools
        jdk 'JDK-17'
        maven 'Maven-3.9'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out source code from GitHub...'
                // Code checkout is automatically handled by Pipeline script from SCM
            }
        }

        stage('Build') {
            steps {
                echo 'Building Java project...'
                bat 'mvn clean compile'
            }
        }

        stage('Unit Test') {
            steps {
                echo 'Running unit tests...'
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                bat 'mvn package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                echo 'Application successfully packaged and ready for deployment!'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}