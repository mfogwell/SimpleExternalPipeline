#!groovy
node(){
    properties([gitLabConnection('FAKE'), [$class: 'JobRestrictionProperty'], pipelineTriggers([pollSCM('* * * * *')])])
    Thread.sleep(100000)
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Linux', submoduleCfg: [], userRemoteConfigs: [[credentialsId: '6a0d658a-7b66-4377-810b-3a7825fff3a4', url: 'https://github.com/alexanderrtaylor/SharedJenkinsLibrary']]])

}
