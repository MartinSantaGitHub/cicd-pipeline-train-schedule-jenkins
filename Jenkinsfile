pipeline {
    agent any

    stages {
        stage('Check Gradle Version') {
            steps {
                sh './gradlew --version'
            }
        }

        stage('Build with Gradle Wrapper') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Create Zip') {
            steps {
                sh './gradlew zip'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive the zip file after it is generated
                archiveArtifacts artifacts: 'build/dist/trainSchedule.zip', allowEmptyArchive: true
            }
        }
    }
}
