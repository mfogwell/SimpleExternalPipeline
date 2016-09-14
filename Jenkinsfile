<flow-definition plugin="workflow-job@2.5">
<actions/>
<description/>
<keepDependencies>false</keepDependencies>
<properties>
<org.jenkinsci.plugins.workflow.job.properties.PipelineTriggersJobProperty>
<triggers/>
</org.jenkinsci.plugins.workflow.job.properties.PipelineTriggersJobProperty>
<jenkins.model.BuildDiscarderProperty>
<strategy class="hudson.tasks.LogRotator">
<daysToKeep>-1</daysToKeep>
<numToKeep>5</numToKeep>
<artifactDaysToKeep>-1</artifactDaysToKeep>
<artifactNumToKeep>-1</artifactNumToKeep>
</strategy>
</jenkins.model.BuildDiscarderProperty>
</properties>
<definition class="org.jenkinsci.plugins.workflow.cps.CpsFlowDefinition" plugin="workflow-cps@2.12">
<script>node(){ sh 'echo "Testing"' }</script>
<sandbox>true</sandbox>
</definition>
<triggers/>
</flow-definition>
