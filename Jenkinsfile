node(){
stage('Checking out code') {
            def scmVars = checkout scm
            user = sh(script: "git log -1 --pretty=format:'%an' ${scmVars.GIT_COMMIT}", returnStdout: true).trim()
        }
}
