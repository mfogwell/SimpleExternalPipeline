#!groovy
import hudson.model.JobProperty;

//properties([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
//def versionDef = new StringParameterDefinition('Version', '', 'The version in BAMS (e.g. 0.0.24)')
//def relBranch = new StringParameterDefinition('ReleaseBranch', 'master', 'Branch to be built - master or release branch')
//properties ([[$class: 'ParametersDefinitionProperty', parameterDefinitions: [versionDef, relBranch]]])


node(){
    echo displayProps().toString()
    //JobProperty jobProperties = displayProps()
    //jobProperties.add([parameters([string(defaultValue: '', description: '', name: 'TestString')]), pipelineTriggers([])])
    //properties(jobProperties)
}

@NonCPS
def displayProps(){
    def jobs = Jenkins.instance.getAllItems()
    jobs.each(){
        if (it.getAbsoluteUrl().equals(env.JOB_URL))
        {
            JobProperty currentProperties = it.getAllProperties()
            return currentProperties
        }
        else{
            return null
        }
    }
}
