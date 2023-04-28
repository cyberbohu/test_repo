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
		stage('Docker Pushing'){
			agent any
			steps{
				withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]){
					sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
					sh "docker push cyberbohu/test-image:latest"
				}
			}
		}
	}
}
