node('ubuntu18.04-OnDemand'){

stage('scm checkout'){
  checkout scm
}

stage('build cri package'){
  sh 'cd cri; mvn clean package'
}

stage('archeive artifacts'){
  sh '''
    mkdir -p $WORKSPACE/CRI
    cp -r cri/device/target/device*.jar CRI
    cp -r cri/owner/target/owner*.war CRI
    cp -r cri/rendezvous/target/rendezvous*.war CRI
    cp -r cri/to0client/target/to0client*.jar CRI
    '''
    zip zipFile: 'CRI.zip', archive: false, dir: 'CRI'
    archiveArtifacts artifacts: 'CRI.zip', fingerprint: true, allowEmptyArchive: false
}

}
