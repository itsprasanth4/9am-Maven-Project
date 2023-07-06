pipeline{
	agent any 
	tools
	{
		maven "Maven"
	}
	stages {
		stage ('checkout')
		{
			steps{
				git branch: 'main', url:' https://github.com/itsprasanth4/java-app.git'
			}
		}

		stage('Execute Maven'){
			steps {
				sh 'mvn package'
			}

		}
		stage('Build Docker Image'){
			steps{
			sh 'docker build -t java-web-app:latest .'
			sh 'docker tag java-web-app itsprasanth4/java-web-app:latest'
		}
}
		stage('Pushing the image to Docker Hub'){
			steps{
				withDockerRegistry([credentialsId:"dockerHub",url: " "])
				{
					sh 'docker push itsprasanth4/java-web-app:latest'
				}
			}
}
		
		
	}
}
