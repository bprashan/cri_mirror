// This job will be restricted to run only on 'ubuntu18.04-OnDemand' Build machine
node('ubuntu18.04-OnDemand'){

// Stage for checking out the sourceCode
stage('scm checkout'){
  cleanWs()
  checkout scm
}

// Stage to build the project
stage('build cri package'){
  sh 'mvn clean package'
}

// Stage to create the cri package and archive
stage('archive artifacts'){
    sh "tar -czvf pri.tar.gz demo/"
    archiveArtifacts artifacts: 'pri.tar.gz', onlyIfSuccessful: true
}

}
