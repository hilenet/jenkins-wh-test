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
                    args '-v /var/jenkins_home/.m2:/root/.m2 --entrypoint=""'
                }
            }
            steps {
                script {
                  sh 'printenv'
                  sh 'slug -l .'
                }
            }
        }
    }
}
