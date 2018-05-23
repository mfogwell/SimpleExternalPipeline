node("lxc-fedora25") { 

  ws("${env.WORKSPACE}/test") {

    stage('CHECKOUT') { 
      checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], gitTool: 'System Git', submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/alexanderrtaylor/SharedJenkinsLibrary']]]
    } 

    stage('IVY CONFIG') { 
      input 'hello' 
        sh "touch testfile"
      input 'hello' 
        sh "ls -la"
    } 
  } 

}
