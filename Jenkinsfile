pipeline {	
	agent any
	stages {
	      stage('Cloning Git') {
	        steps {
	              checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/prasad-midde/git-secret-scan.git']]])
	        }
	       }
	    stage('git-secrets-check') {
	         steps {
            sh "git init"
            sh "git secrets --install"
            sh "git secrets --list"
            sh "git secrets --register-aws"
            sh "git secrets --list"
            sh "git secrets --add 'MyPASSWORD[0-9]+'"
	          sh "git secrets --scan -r"
	      }
	    }
	
	}
	}
