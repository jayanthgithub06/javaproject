pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install node modules') {
            steps {
                bat 'npm install'
            }
        }

        stage('Running tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Building app') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploying app') {
            environment {
                PATH = "$PATH:C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\HelloWorldPipelineAsCode\\.npm\\_npx\\5f7878ce38f1eb13\\node_modules\\pm2\\bin"
            }
            steps {
                bat 'pm2 serve build 4002 --watch'
            }
        }
    }
}
