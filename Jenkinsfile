node("lxc-fedora25") { 

  ws("${env.WORKSPACE}/test") {

    stage('CHECKOUT') { 
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/alexanderrtaylor/SharedJenkinsLibrary']]])
    } 

    stage('IVY CONFIG') { 
      input 'hello' 
        sh "touch testfile"
      input 'hello' 
    } 
  } 

}
