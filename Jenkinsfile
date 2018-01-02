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
                sh "chmod 777 /Fake:Name/script.sh"
                sh './Fake:Name/script.sh'
            }
        }
    }
}
