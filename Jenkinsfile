#!groovy
properties([
    pipelineTriggers([
        triggers: [
            [
                $class: 'jenkins.triggers.ReverseBuildTrigger',
                upstreamProjects: "/Jobs/pipelines/EXP/auto/ttm_cli/master",
                threshold: hudson.model.Result.SUCCESS
            ]
        ]
    ]),
    [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false]
])

sh 'echo "success"'
