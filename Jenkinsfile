pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Node.js setup') {
            steps {
                sh './gradlew nodeSetup'
            }
        }
        stage('Install dependencies') {
            steps {
                sh './gradlew npmInstall'
            }
        }
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
    }
}
