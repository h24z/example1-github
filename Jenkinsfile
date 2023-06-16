pipeline {
	agent none  stages {
    stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker build -t agus3yoga/jenkins-builder:dev-latest .'
      }
    }
    stage('Docker Push') {
    	agent any
      steps {
      	withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'DockerhubPassword', usernameVariable: 'DockerhubUser')]) {
        	sh "docker login -u ${env.DockerhubUser} -p ${env.DockerhubPassword}"
          sh 'docker push agus3yoga/jenkins-builder:dev-latest'
        }
      }
    }
  }
}
