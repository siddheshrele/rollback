pipeline {
  agent any
  parameters {
    //exclude to show critical branches  
    //gitParameter branchFilter: 'origin/(?!.*master)(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'	  
  }
  stages {
    stage('Initalize the branches names') {
      steps {
        git branch: "${params.BRANCH}", url: 'https://github.com/siddheshrele/rollback.git'
      }
    }
    stage('Check Out Rollbackbuild') {
      steps {
        git branch: '${BRANCH}', credentialsId: 'jenk_git', url: 'https://github.com/siddheshrele/rollback.git'
      }
    }
    stage('Deploying the build') {
      steps {
        sh 'pwd'
	    sh 'ls -lha'
	    sh 'cat version.txt'
      }
    }    
    
  }
}
