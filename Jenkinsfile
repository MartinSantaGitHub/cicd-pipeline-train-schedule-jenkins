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

        stage('Node.js setup') {
            steps {
                sh './gradlew nodeSetup'
            }
        }

        stage('Clear npm cache') {
            steps {
                sh 'npm cache clean --force'
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
