pipeline {
    agent any
    
    environment {
        PATH = "C:\\Program Files\\Git\\cmd;${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git 'https://github.com/jayanthgithub06/javaproject.git'
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jayanthgithub06/javaproject.git']]])
                }
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
                bat 'npx pm2 serve build 4005 --watch'
            }
        }
    }
}
