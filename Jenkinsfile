#!groovy

properties([gitLabConnection(pipelineTriggers([githubPush(), pollSCM('')])])

node() {
   
   stage('CHECKOUT') { 
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'AlexGithub', url: 'https://github.com/alexanderrtaylor/subversion-plugin']]])
   } 
    
   stage('BUILD') {
      echo 'in build stage'
   }

   stage('REPORTS') {
      echo 'REPORTS'
   }
}
