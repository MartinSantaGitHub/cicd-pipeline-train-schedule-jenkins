pipeline {
    agent any

    stages {
        stage('Check Gradle Version') {
            steps {
                sh './gradlew --version'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Gradle Wrapper') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Node.js Setup') {
            steps {
                sh './gradlew nodeSetup'
            }
        }

        stage('Install Node Dependencies') {
            steps {
                sh './gradlew npmInstall'
            }
        }

        stage('Build with npm') {
            steps {
                sh './gradlew npmBuild'
            }
        }

        stage('Run Tests with npm') {
            steps {
                sh './gradlew npmTest'
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
