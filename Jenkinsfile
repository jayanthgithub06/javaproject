pipeline {
    agent any
    stages {
        stage('Install Node modules') {
            steps {
                // Clean up node_modules before installing to ensure a fresh install
                sh "rm -rf node_modules"
                sh "npm install"
            }
        }
        stage('Running tests') {
            steps {
                // Run tests with npm test
                sh "npm test"
            }
        }
        stage('Building app') {
            steps {
                // Run the build process
                sh "npm run build"
            }
        }
        stage('Deploying app') {
            steps {
                // Use pm2 to serve the built app
                sh 'pm2 serve build 4005 --watch'
            }
        }
    }
}
