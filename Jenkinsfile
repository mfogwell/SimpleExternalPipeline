pipeline {
    agent none
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            agent any
            steps {
                echo "Building"
            }
        }
        stage('Test') {
            agent any
            steps {
                sh "chmod 777 Fake:Name/script.sh"
                sh './Fake:Name/script.sh'
            }
        }
    }
}
