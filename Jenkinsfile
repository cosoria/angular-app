pipeline {
  agent any
  environment {
    COURSE = 'Calgary DevOps'
    BRANCH = 'main'
    WWWROOT = '/var/www/html'
    SSHUSER = 'cosoria'
  }
  stages {
    stage('Audit Tools') {
      steps {
        echo "Audit all tools to be use on this pipeline ${BRANCH}"
        sh "git --version"
        sh "node --version"
        sh "npm --version"
        sh "ng --version"
        sh "ansible --version"
        echo "Workspace Folder: ${WORKSPACE}"
      }
    }
    stage('Install packages') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
          echo "Install conduit UI packages"
          sh "npm install"
        }
      }
    }
    stage('Run linting') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
          sh "npm run lint"
        }
      }
    }
    stage('Build UI') {
      steps {
        dir("${WORKSPACE}/conduit-ui") {
          sh "npm run build"
        }
      }
    }
    stage('Copy File To WEB01') {
      steps {
          sh "ssh web01 ls -l ${WWWROOT}"
          sh "ssh api01 ls -l ${WWWROOT}"
      }
    }
  }
}