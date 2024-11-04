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
        docker login -u jiho9898 -p Rladudwns98!
        docker build -t jiho9898/projectlab:jenkins .
        docker push jiho9898/projectlab:jenkins
        '''
      }
    }
  }
}
