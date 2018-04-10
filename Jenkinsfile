pipeline {
    agent none
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            agent Any
            steps {
                echo "Building"
            }
        }
        stage('Test') {
            agent {label 'TestAgent'}
            steps {
                sh "chmod 777 Fake:Name/script.sh"
                sh './Fake:Name/script.sh'
            }
        }
    }
}
