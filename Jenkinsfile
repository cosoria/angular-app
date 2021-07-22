pipeline {
  agent any
  environment {
    COURSE = 'DevOps Calgary'
    BRANCH = 'main'
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
      }
    }
    stage('Install packages') {
		echo "Install conduit UI packages"
		sh "npm install"
    }
  }
}