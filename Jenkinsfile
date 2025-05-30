pipeline {
    agent any

    tools {
        maven 'maven -3.9.6'  // Name from Global Tool Configuration
    }

    environment {
        BUILD_ENV = "production"
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-creds', url: 'https://github.com/saitejadevops96/maven-standalone-application.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}

