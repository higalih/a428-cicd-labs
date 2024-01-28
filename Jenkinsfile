pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 4000:3000' 
        }
    }
    
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
       stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
       stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai menggunakan React Apps? (Klik "Proceed" untuk mengakhiri)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}