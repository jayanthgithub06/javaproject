pipeline {
    agent any

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }
    
    stages {
        stage ('node info') {
            steps {
                bat "npm config ls"
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
                bat 'C:\Users\jayanth\AppData\Roaming\npm\pm2.cmd npx pm2 serve build 4005 --watch'
            }
        }
    }
}
