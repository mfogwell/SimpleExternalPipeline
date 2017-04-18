#!groovy

properties([gitLabConnection('FAKE'), [$class: 'JobRestrictionProperty'], pipelineTriggers([githubPush(), pollSCM('')])])

node() {
   
   stage('CHECKOUT') { 
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e7799e4e-2ef5-4b2f-a17c-d8a024ce47c4', url: 'https://github.com/alexanderrtaylor/subversion-plugin']]])
   } 
    
   stage('BUILD') {
      echo 'in build stage'
   }

   stage('REPORTS') {
      echo 'REPORTS'
   }
}
