pipeline {
    agent any
    parameters {
        gitParameter name: 'TAG', 
                     type: 'PT_TAG',
                     defaultValue: 'master'
    }
    stages {
        stage('Example') {
            steps {
                checkout([$class: 'GitSCM', 
                          branches: [[name: "${params.TAG}"]], 
                          doGenerateSubmoduleConfigurations: false, 
                          extensions: [], 
                          gitTool: 'Default', 
                          submoduleCfg: [], 
                          userRemoteConfigs: [[url: 'https://github.com/siddheshrele/rollback.git']]
                        ])
            }
        }
		stage('Deploying the build') {
			steps {
					sh 'pwd'
					sh 'ls -lha'
					sh 'cat version.txt'
				sh 'git tag --contains ${GIT_COMMIT}'
			}
		} 
    }
}
