pipeline{
    agent any
    stages{
        stage('install node modules')
        steps{
            sh "npm install"
        }
    }
    stage('Running tests'){
        steps{
            sh "npm test"
        }
    }
    stage('Building app'){
        steps{
            sh"npm run build"
        }
    }
    stage('deploying app'){
        steps{
            sh 'pm2 serve build 4005 --watch'
        }
    }

}
