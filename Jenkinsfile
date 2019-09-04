pipeline {
	agent any
	stages {
		stage('Clean Workspace') {
			steps {
				cleanWs()
			}
		}
		stage('gitStage') {
			steps{
				git 'https://github.com/augustinetom17/jenkins-tut.git'
			}
		}
		stage ('Compile and Build') {
			steps {
				sh label: '', script: '''ant -version
				ant -f build.xml'''
			}
		}
	}
}

