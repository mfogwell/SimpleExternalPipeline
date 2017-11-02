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
    def jobs = Jenkins.instance.getAllItems()
    jobs.each(){
        echo env.JOB_URL
        if (it.getUrl().equals(env.JOB_URL))
        {
            def currentProperties = it.getProperties()
            currentProperties.each(){
                echo it.toString()
            }
        }
    }
}
