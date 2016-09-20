echo 'branch: '
echo env.GIT_BRANCH

node {

stage 'Checkout'
checkout scm

stage 'Build & Test'
try
{
sh '''ARTIFACTORY_URL=http://artifactory.sys.ch3pcf04.express-scripts.com/artifactory
GENERIC_LOCAL_URL=$ARTIFACTORY_URL"/generic-local/node-modules"
export SASS_BINARY_SITE=$GENERIC_LOCAL_URL"/node-sass/binaries"
export PHANTOMJS_CDNURL=$GENERIC_LOCAL_URL"/phantomjs/binaries"
NPM_VIRTUAL_URL=$ARTIFACTORY_URL"/api/npm/npm-virtual"
npm install
gulp validate'''

} catch (e) {

}

sh "echo Build Complete"
stage 'Publish'
//Testing may be in the maven build results, or maybe performed here.
//Use this section for reporting results.
sh "echo Test Complete"
stage 'Publish'
input id: 'Publish', message: 'Wait for XL Release Approval'
stage 'Deploy QA'
input id: 'DeployQA', message: 'Waiting for XL Release Approval to Publish'
stage 'Validate QA'

}
