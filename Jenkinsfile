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
		stage ('Copying Artifact') {
			steps { 
				sh '''
				mkdir /var/lib/jenkins/workspace/ant-build-pipeline/artifact
				cp /var/lib/jenkins/workspace/ant-build-pipeline/dist/*.jar /var/lib/jenkins/workspace/ant-build-pipeline/artifact/
				'''
			}
		}
		stage ('Copy Artifact using plugin') {
			script {
                 step ([$class: 'CopyArtifact',
                 projectName: 'ant-build-pipeline',
                 filter: "/var/lib/jenkins/workspace/ant-build-pipeline/dist/*.jar",
                 target: '/var/lib/jenkins/workspace/ant-build-pipeline/artifact-new/']);
			}	 
		}	
			
	}
}
