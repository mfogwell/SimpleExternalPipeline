#!groovy
import hudson.model.JobProperty;

//properties([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
//def versionDef = new StringParameterDefinition('Version', '', 'The version in BAMS (e.g. 0.0.24)')
//def relBranch = new StringParameterDefinition('ReleaseBranch', 'master', 'Branch to be built - master or release branch')
//properties ([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [versionDef, relBranch]]])


node(){
    def jobProperties = displayProps()
    echo "success 1"
    jobProperties.add([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
    echo "success 2"
    properties(<JobProperty> jobProperties)
}

@NonCPS
def displayProps(){
    def jobs = Jenkins.instance.getAllItems()
    jobs.each(){
        if (it.getAbsoluteUrl().equals(env.JOB_URL))
        {
            def currentProperties = it.getProperties()
            return currentProperties
        }
    }
}
