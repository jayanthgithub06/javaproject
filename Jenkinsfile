pipeline {
    agent any

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }
    
    stages {
        stage ('Declarative: Checkout SCM') {
            steps {
                script {
                    // Checkout the code from the repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jayanthgithub06/javaproject.git']]])

                    // Delete the index.lock file
                    bat 'del .git\\index.lock'
                }
            }
        }
        
        stage ('Node Info') {
            steps {
                bat "npm config ls"
            }
        }
        
        stage ('Install Node Modules') {
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
                // Use pm2 to serve the build folder
                bat 'npx pm2 serve build 4005 --watch'
            }
        }
    }
}
