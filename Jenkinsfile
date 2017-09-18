node('master') {
  stage('Unit Tests') {
    git url: "https://github.com/bobbydeveaux/micro-nats.git"
  }
  stage('Build Image') {
    sh "oc start-build nats --from-file=. --follow"
  }
  stage('Deploy') {
    openshiftDeploy depCfg: 'nats', namespace: 'fbac'
    openshiftVerifyDeployment depCfg: 'nats', replicaCount: 1, verifyReplicaCount: true
  }
}