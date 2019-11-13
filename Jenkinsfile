pipeline {
  agent none

  parameters {
    string (
      name: 'payload',
    )
  }

  stages {
    stage('deploy') {
      agent {
        docker {
          image '030482650818.dkr.ecr.ap-northeast-1.amazonaws.com/slug'
          registryUrl 'https://030482650818.dkr.ecr.ap-northeast-1.amazonaws.com/slug'
          args '-v /var/jenkins_home/.m2:/root/.m2 --entrypoint="" -u root'
        }
      }
      environment {
        SSH_KEY = credentials('proxy-private')
        JENKINS_CRED = credentials('hilenet-cred')
      }
      steps {
        script {
          sh 'cp $SSH_KEY /tmp/hoge'
          sh 'slug -l .'
          sh 'mkdir -p /tmp/fuga'
          sh 'touch /tmp/fuga/bar'
          archiveArtifacts artifacts: /tmp/fuga/*
        }
      }
    }
  }
}
