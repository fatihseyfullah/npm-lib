pipeline {
    agent any
    
    tools {
        nodejs 'nodejs' 
    }
    
    environment {
        NPM_TOKEN = credentials('npm-token') 
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/fatihseyfullah/npm-lib.git'
            }
        }
        
        stage('Setup') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install' 
            }
        }
        
        
        stage('Publish to NPM') {
            steps {
                script {

                  sh 'echo "//registry.npmjs.org/:_authToken=${NPM_TOKEN}" > .npmrc'
                    
                  sh 'npm publish'
                    
                  sh 'rm -f .npmrc'
                }
            }
        }
    }
    
}
