pipeline {
    agent any
 
    // Configuration options applicable to the entire job
    options {
        // This build should not take long, fail the build if it appears stuck
        timeout(time: 5, unit: 'MINUTES')
 
        // Don't fill up the build server with unnecessary cruft
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
 
    environment {
        REPOSITORY = "cray"
        IMAGE_PREFIX = "cray"
        APP = "ars"
        VERSION = sh(returnStdout: true, script: "cat .version").trim()
        GIT_TAG = sh(returnStdout: true, script: "git rev-parse --short HEAD").trim()
        IMAGE_TAG = "v${VERSION}-${BUILD_NUMBER}-${GIT_TAG}"
        IMAGE = "${CRAY_DOCKER_REGISTRY}/${REPOSITORY}/${IMAGE_PREFIX}-${APP}:${IMAGE_TAG}"
    }
 
    stages {
        stage('Prep') {
            // Remove existing 'build' directory and recreate it
         
            steps{
                echo "hello Prep"
            }
        }
 
        stage('Checkout') {
            steps { checkout scm }
        }
 
        // Generate docker image
        stage('Build') {
            steps{
                echo "hello Build"
            }
            
        }
 
        // Publish
        stage('Publish: Master') {
            // For Master branch builds, send the artifacts to the artifact repository and internal docker registry
            when { branch 'master' }
            steps{
                echo "hello Publish"
            }
        }
    }
 
    post('Post-build steps') {
        // Clean up the local build registry whether the build was successful or not
        always {
            echo "post build"
        }
        success {
            archiveArtifacts artifacts: 'build/*', fingerprint: true
        }
        // notify is a DST-provided function
        failure {
            echo "failure!"
        }
    }
}
