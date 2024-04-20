pipeline {
    agent any

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
        PM2_PATH = "C:\\Users\\jayanth\\AppData\\Roaming\\npm\\pm2.cmd"
    }

    stages {
        stage ('node info') {
            steps {
                sh "npm config ls"
            }
        }
        stage ('Install node modules') {
            steps {
                bat "npm install"
            }
        }
        stage('Running tests'){
            steps {
                bat "npm test"
            }
        }
        stage('Building app'){
            steps {
                bat "npm run build"
            }
        }
        stage('Deploying app') {
            steps {
                bat "${env.PM2_PATH} serve build 4005 --watch"
            }
        }
    }
}
