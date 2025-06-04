pipeline {
	agent any
	tools {
		maven 'Maven'
	}
	environment{
		LANG='en_US.UTF-8'
		LC_ALL='en_US.UTF-8'
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'master', url: 'https://github.com/HarshiB2005/MawaPrac.git'
			}
		}
		
		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
		
		stage('Archieve') {
			steps {
				archetypeArtifacts artifacts: 'target/*.war', fingerprint:true
			}
		}
		
		stage('Deploy') {
			steps {
				sh 'mvn clean package'
				sh 'ansible-playbook playbook.yml -i hosts.ini'
			}
		}
	}
}
