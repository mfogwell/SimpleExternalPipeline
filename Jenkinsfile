node() { 

  ws("/Volumes/WorkSD/CloudBees/cases/workspace") {

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
