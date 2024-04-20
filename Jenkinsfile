pipeline {
    agent any

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
        PATH = "$PATH:E:\\work\\ReactApp1\\node_modules\\.bin"
    }

    stages {
        stage('node info') {
            steps {
                sh "npm config ls"
            }
        }

        stage('Install node modules') {
            steps {
                sh "npm install"
            }
        }

        stage('Running tests') {
            steps {
                sh "npm test"
            }
        }

        stage('Building app') {
            steps {
                sh "npm run build"
            }
        }

        stage('Deploying app') {
            steps {
                sh 'E:\\work\\ReactApp1\\node_modules\\.bin\\pm2 serve build 4005 --watch'
            }
        }
    }
}
