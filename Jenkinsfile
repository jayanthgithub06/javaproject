pipeline {
    agent any

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
        PATH = "$PATH:E:\\work\\ReactApp1\\node_modules\\.bin"
    }

    stages {
        stage('Node Info') {
            steps {
                bat "npm config ls"
            }
        }

        stage('Install Node Modules') {
            steps {
                bat "npm install"
            }
        }

        stage('Running Tests') {
            steps {
                bat "npm test"
            }
        }

        stage('Building App') {
            steps {
                bat "npm run build"
            }
        }

        stage('Deploying App') {
            steps {
                script {
                    def pathToPM2 = bat(script: "where pm2", returnStdout: true).trim()
                    if (pathToPM2) {
                        bat "start ${pathToPM2} serve build 4005 --watch"
                    } else {
                        echo "PM2 is not installed, please install it."
                    }
                }
            }
        }
    }
}
