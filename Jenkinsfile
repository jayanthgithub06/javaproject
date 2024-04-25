pipeline {
    agent any

    environment {
        // Set npm cache directory
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }

    stages {
        stage('Node Info') {
            steps {
                bat 'npm config ls'
            }
        }
        stage('Install Node Modules') {
            steps {
                bat 'npm install'
            }
        }
        stage('Running Tests') {
            steps {
                bat 'npm test'
            }
        }
        stage('Building App') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Deploying App') {
            steps {
                // Serve the build directory using pm2
                bat 'pm2 serve build 4005 --watch'
            }
        }
    }
}
