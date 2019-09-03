node('master') {
	stage('gitStage') {
     git 'https://github.com/augustinetom17/jenkins-tut.git'
	}
	stage('Build and Deploy') {
		withAnt(installation: 'Ant', jdk: 'JDK-1.8') {
		bat label: '', script: 'ant -f build.xml'
		}
	}
}
