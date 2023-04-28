pipeline{
	agent none
	
	stages{
		stage('Build'){
			agent{
				docker{
					image 'node:alpine'
					args '-p 3000:3000'
				}
			}
			steps {
				sh 'npm install'
			}
		}
		stage("Docker Build"){
			agent any
			steps {
				sh 'docker build -t cyberbohu/test-image:latest .'
			}
		}
	}
}
