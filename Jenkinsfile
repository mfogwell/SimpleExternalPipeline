#!groovy

properties([gitLabConnection(pipelineTriggers([githubPush(), pollSCM('')])])

node() {
   
   stage('CHECKOUT') { 
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'bca4ce0b-ac98-44a8-9ac5-6fd0b6e4495d', url: 'https://github.com/alexanderrtaylor/subversion-plugin']]])
   } 
    
   stage('BUILD') {
      echo 'in build stage'
   }

   stage('REPORTS') {
      echo 'REPORTS'
   }
}
