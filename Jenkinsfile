#!groovy
properties([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
def versionDef = new StringParameterDefinition('Version', '', 'The version in BAMS (e.g. 0.0.24)')
def relBranch = new StringParameterDefinition('ReleaseBranch', 'master', 'Branch to be built - master or release branch')
properties ([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [versionDef, relBranch]]
])


node(){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Linux', submoduleCfg: [], userRemoteConfigs: [[credentialsId: '6a0d658a-7b66-4377-810b-3a7825fff3a4', url: 'https://github.com/alexanderrtaylor/SharedJenkinsLibrary']]])
}
