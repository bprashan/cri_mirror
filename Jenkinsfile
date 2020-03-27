node('ubuntu18.04-OnDemand'){

stage('scm checkout'){
  checkout scm
}

stage('build cri package'){
  sh 'mvn clean package'
}

stage('archeive artifacts'){
  sh '''
    mkdir -p $WORKSPACE/cri
    cp -r cri/device/target/device*.jar cri
    cp -r cri/owner/target/owner*.war cri
    cp -r cri/rendezvous/target/rendezvous*.war cri
    cp -r cri/to0client/target/to0client*.jar cri
    '''
    zip zipFile: 'cri.zip', archive: false, dir: 'cri'
    archiveArtifacts artifacts: 'cri.zip', fingerprint: true, allowEmptyArchive: false
}

}
