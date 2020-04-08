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
  sh '''
    mkdir -p $WORKSPACE/cri
    cp -r device/target/device*.jar cri
    cp -r owner/target/owner*.war cri
    cp -r rendezvous/target/rendezvous*.war cri
    cp -r to0client/target/to0client*.jar cri
    '''
    zip zipFile: 'cri.zip', archive: false, dir: 'cri'
    archiveArtifacts artifacts: 'cri.zip', fingerprint: true, allowEmptyArchive: false
    cleanWs()
}

}
