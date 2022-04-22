pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/hwi999/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t whgnlwp2011/testweb:newnewmain .
        sudo docker push whgnlwp2011/testweb:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
	sudo kubectl set image deployment deploy-main ctn-main=whgnlwp2011/testweb:newnewmain
        '''
      }
    }
  }
}
