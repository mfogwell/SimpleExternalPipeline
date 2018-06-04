// Jenkinsfile for CMS Artifact Repository Service
// Copyright 2018 Cray Inc. All rights reserved.
 
////////////////////////////////////////// JENKINS SHARED LIBRARY //////////////////////////////////////////

// Library repo: https://stash.us.cray.com/projects/DST/repos/jenkins-shared-library

// Transfers the build artifact(s) to iyumcf's DST yum repository
// If the branch is master: /var/www/html/dstrepo/dev
// If the branch isn't master: /var/www/html/dstrepo/predev
//def transfer = new com.cray.Transfer()

// This sends out an email to a user or users in a git project after the build is over
// Similar to the 'notify' function it contains the job name and build url
// It also includes git commit diff, revision changes, and more
//def mail = new com.cray.Mail()
//////////////////////////////////////// END JENKINS SHARED LIBRARY ////////////////////////////////////////

pipeline {
    agent any
 
    // Configuration options applicable to the entire job
    options {
        // This build should not take long, fail the build if it appears stuck
        timeout(time: 5, unit: 'MINUTES')
 
        // Don't fill up the build server with unnecessary cruft
        buildDiscarder(logRotator(numToKeepStr: '10'))
 
        // Add timestamps and color to console output, cuz pretty
        //timestamps()
    }
 
    environment {
        REPOSITORY = "cray"
        IMAGE_PREFIX = "cray"
        APP = "ars"
        //VERSION = sh(returnStdout: true, script: "cat .version").trim()
        //GIT_TAG = sh(returnStdout: true, script: "git rev-parse --short HEAD").trim()
        IMAGE_TAG = "v${VERSION}-${BUILD_NUMBER}-${GIT_TAG}"
        IMAGE = "${CRAY_DOCKER_REGISTRY}/${REPOSITORY}/${IMAGE_PREFIX}-${APP}:${IMAGE_TAG}"
    }
 
    stages {
        stage('Prep') {
            // Remove existing 'build' directory and recreate it
            steps { dir("build") { deleteDir(); sh "mkdir -p build" } }
        }
 
        stage('Checkout') {
            steps { checkout scm }
        }
 
        // Generate docker image
        stage('Build') {
            environment {
                BUILD_DATE = sh(returnStdout: true, script: "date +'%Y-%m-%dT%H:%M:%S'").trim()
            }
            steps {
                sh """
                    docker build --tag '${IMAGE}' --build-arg VCS_REF=${GIT_TAG} --build-arg VERSION='${IMAGE_TAG}' --build-arg BUILD_DATE='${BUILD_DATE}' .
                    docker save "${IMAGE}" | gzip -c > build/${APP}.tar.gz
                """
            }
        }
 
        // Publish
        stage('Publish: Master') {
            // For Master branch builds, send the artifacts to the artifact repository and internal docker registry
            when { branch 'master' }
            steps {
                sh "docker push ${IMAGE}"
                sh "echo ${IMAGE_TAG} > build/version"
                sh "docker tag ${IMAGE} ${CRAY_DOCKER_REGISTRY}/${REPOSITORY}/${IMAGE_PREFIX}-${APP}:latest"
                sh "docker push ${CRAY_DOCKER_REGISTRY}/${REPOSITORY}/${IMAGE_PREFIX}-${APP}:latest"
                //script {
                    //transfer.artifact("build/*.tar.gz")
                    //transfer.artifact("build/version")
                //}
            }
        }
    }
 
    post('Post-build steps') {
        // Clean up the local build registry whether the build was successful or not
        always {
            sh(returnStdout: true, script: "docker rmi ${IMAGE}")
        }
        success {
            archiveArtifacts artifacts: 'build/*', fingerprint: true
        }
        // notify is a DST-provided function
        failure {
         echo "failure"
            //script {
                //mail.build_status('fail', "Failed: ${env.JOB_NAME}")
            //}
        }
    }
}
