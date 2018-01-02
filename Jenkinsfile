pipeline {
    agent any 
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building"
            }
        }
        stage('Test') {
            steps {
                sh './Fake:Name/script.sh'
            }
        }
    }
}
