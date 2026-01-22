pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root -v /var/www:/var/www'
        }
    }

    environment {
        PROD_DIR = '/var/www/krestyaninov'
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build production') {
            steps {
                sh 'npm run build_prod'
            }
        }
        stage('Deploy to production') {
            steps {
                sh '''
                    mkdir -p ${PROD_DIR}
                    rm -rf ${PROD_DIR}/*
                    cp -r dist/* ${PROD_DIR}/
                '''
            }
        }
    }
}
