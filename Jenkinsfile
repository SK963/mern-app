pipeline {
    agent any

    environment {
        BACKEND_DIR = 'backend'
        FRONTEND_DIR = 'frontend'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sk963/mern-app.git'
            }
        }

        stage('Install Backend') {
            steps {
                dir("${env.BACKEND_DIR}") {
                    sh 'npm install'
                }
            }
        }

        stage('Test Backend') {
            steps {
                dir("${env.BACKEND_DIR}") {
                    sh 'npm test'
                }
            }
        }

        stage('Install Frontend') {
            steps {
                dir("${env.FRONTEND_DIR}") {
                    sh 'npm install'
                }
            }
        }

        stage('Test Frontend') {
            steps {
                dir("${env.FRONTEND_DIR}") {
                    sh 'npm test'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir("${env.FRONTEND_DIR}") {
                    sh 'npm run build'
                }
            }
        }

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'frontend/build/**', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
            }
        }
    }
}
