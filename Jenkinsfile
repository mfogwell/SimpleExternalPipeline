#!groovy


//properties([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
//def versionDef = new StringParameterDefinition('Version', '', 'The version in BAMS (e.g. 0.0.24)')
//def relBranch = new StringParameterDefinition('ReleaseBranch', 'master', 'Branch to be built - master or release branch')
//properties ([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [versionDef, relBranch]]])


node(){
    displayProps()
}

@NonCPS
def displayProps(){
    def currentProperties = currentBuild.getProperties()
    currentProperties.each(){
        echo "Property 1"
        echo it.getDisplayName()
    }
}
