pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/mitesh51/AntExample.git', branch: 'master', poll: true)
      }
    }
    stage('Build') {
      steps {
        script {
          def antHome = tool 'apache-ant-1.10.5';
          bat "${antHome}/bin/ant -d clean war"
        }

        archiveArtifacts(artifacts: '**/*.war', onlyIfSuccessful: true)
      }
    }
  }
}