pipeline {
    agent any
    
    environment {
        NETLIFY_SITE_ID = '2fe7c342-15f5-4dce-9a9c-8337968eb3e3'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'npm install -g netlify-cli'
                sh 'netlify deploy --site ${NETLIFY_SITE_ID} --auth ${NETLIFY_AUTH_TOKEN} --prod --dir=build'
            }
        }
    }
}