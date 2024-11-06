pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/jiho989898/projectlab.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        docker login -u admin -p Harbor12345
        docker build -t 211.183.3.100/hk-repo/repository:jiho .
        docker push 211.183.3.100/hk-repo/repository:jiho
        '''
      }
    }
    stage('jenkins -> node') {
      steps {
        sh '''
        ansible-playbook nodebook.yml
        '''
      }
    }
    stage('jenkins -> master') {
      steps {
        sh '''
        ansible-playbook masterbook.yml
        '''
      }
    }
  }
}
